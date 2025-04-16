# SOP: Python Virtual Environment

This document outlines the standard operating procedures (SOPs) for managing Python virtual environments in a common application stack.

## 📌 Purpose

To isolate Python dependencies and avoid conflicts between project packages by using virtual environments.

---

## 🔧 Commands & Usage

### 1. **Creation of Virtual Environment**

```bash
python3 -m venv venv_name
```
- venv_name: Name of the virtual environment directory.

### 2. Activation

```bash
source venv_name/bin/activate
```

- You should see the environment name prefixed in your terminal prompt.

### 3. Package Installation

```bash
pip install <package_name>
```

Install multiple packages via requirements.txt:

```bash
pip install -r requirements.txt
```

### 4. Freezing Installed Packages

```bash
pip freeze > requirements.txt
```
- This saves the exact versions of all installed packages.

### 5. Deactivation

```bash
deactivate
```
- This will return you to the system’s default Python environment.

### 6. Deleting a Virtual Environment

```bash
rm -rf venv_name
```
- Ensure the environment is deactivated before deletion.

---

## ⚠️ Troubleshooting

### ❗ Permission Denied
If you see a permissions error while activating:

```bash
chmod +x venv_name/bin/activate
```

Also consider:

```bash
sudo chown -R $USER venv_name/
```

### ❗ Pip Installation Errors
If packages fail to install due to permissions:

```bash
python3 -m pip install --upgrade pip
```
Make sure virtualenv is active. If still failing, use:

```bash
pip install --user <package_name>
```

### 📂 Recommended Folder Structure

project/
│
├── venv/               # Virtual environment (should be gitignored)
├── src/                # Application source code
├── requirements.txt    # List of dependencies
└── README.md           # This document

### 📝 Notes
- Use .gitignore to exclude the venv/ directory.
- Virtual environments are project-specific; don’t share them across unrelated projects.
- Always regenerate your virtualenv when switching major Python versions.

---

## 🔚 End of SOP

| Date       | Author           | Change Description         |
|------------|------------------|----------------------------|
| 15-Apr-25  | Nishkarsh Kumar  | Initial draft              |

---
