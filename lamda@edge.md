# Lambda@Edge POC with CloudFront

This POC demonstrates how to integrate **Lambda@Edge** with an **Amazon CloudFront** distribution to inject **security headers** into the HTTP responses.  

---

## Architecture

1. **Client Request** → CloudFront Distribution  
2. **Lambda@Edge (Viewer Response)** → Adds security headers  
3. **Origin/Cache Response** → Returned to user with enhanced headers  

---

## Steps

### 1. Create the Lambda Function

- Region: **`us-east-1`** (N. Virginia) → required for Lambda@Edge because CloudFront replicates globally from this region.  
- Runtime: `Node.js 18.x`
- File name: `index.js`
- IAM Role: Attach `AWSLambdaBasicExecutionRole` policy  
- Trust relationships must include both `lambda.amazonaws.com` and `edgelambda.amazonaws.com`:  
  ```json
  {
    "Version": "2012-10-17",
    "Statement": [
      {
        "Effect": "Allow",
        "Principal": {
          "Service": [
            "lambda.amazonaws.com",
            "edgelambda.amazonaws.com"
          ]
        },
        "Action": "sts:AssumeRole"
      }
    ]
  }

### 2. Lambda Function Code

- Save the following as index.js:

```
'use strict';

exports.handler = (event, context, callback) => {
    const response = event.Records[0].cf.response;
    const headers = response.headers;

    // Add security headers
    headers['strict-transport-security'] = [
      { key: 'Strict-Transport-Security', value: 'max-age=63072000; includeSubdomains; preload' }
    ];
    headers['content-security-policy'] = [
      { key: 'Content-Security-Policy', value: "default-src 'none'; img-src 'self'; script-src 'self'; style-src 'self'; object-src 'none'" }
    ];
    headers['x-content-type-options'] = [
      { key: 'X-Content-Type-Options', value: 'nosniff' }
    ];
    headers['x-frame-options'] = [
      { key: 'X-Frame-Options', value: 'DENY' }
    ];
    headers['x-xss-protection'] = [
      { key: 'X-XSS-Protection', value: '1; mode=block' }
    ];
    headers['referrer-policy'] = [
      { key: 'Referrer-Policy', value: 'same-origin' }
    ];

    // Return modified response
    callback(null, response);
};
```

### 3. Publish Lambda Version

Lambda@Edge requires a published version.
From the AWS Lambda console:
- Click Actions → Publish new version.

### 4. Attach to CloudFront

1. Go to **CloudFront** → **Distributions**.  
2. Select your distribution.  
3. Under **Behaviors** → **Edit**.  
4. Add **Lambda function**:  
   - **Event type**: Viewer Response  
   - **Function ARN**: `<your lambda version ARN>`  

### Step 5: Deploy and Verify Changes

1. Wait for **CloudFront** to deploy the updated configuration (~2-7 minutes).  
2. Open your website in a browser and navigate to the **Network** tab in **Developer Tools**.  
3. Reload the page and inspect the **response headers** you added.  

## Conclusion  

Lambda@Edge enables running code closer to users, improving performance, security, and personalization. Beyond this POC, it supports use cases such as SEO optimization, bot mitigation, real-time image transformation, A/B testing, authentication, and user analytics—making it a powerful service for modern, scalable web applications.  
