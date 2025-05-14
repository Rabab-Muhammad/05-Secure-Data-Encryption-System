# 05-Secure-Data-Encryption-System

## Objective 🎯
Develop a **Streamlit-based secure data storage and retrieval system** where:

- Users store data with a unique passkey 🔑.
- Users decrypt data by providing the correct passkey 🔓.
- Multiple failed attempts result in a forced reauthorization (login page) 🔒.
- The system operates entirely in memory without external databases 🧠.

## 🔹 Requirements

### 1. Data Storage (In-Memory Dictionary) 📂
Each entry is stored as:

```python
stored_data = {
    "user1_data": {"encrypted_text": "some_ciphertext", "passkey": "hashed_passkey"},
    ...
}
```


---

### 1. Passkeys Must Be Hashed (e.g., SHA-256) 🔑
- All passkeys must be hashed before storage to ensure security.
- Use hashing algorithms like **SHA-256** to protect user passkeys.

### 2. Secure Encryption & Decryption 🔐
- **Encrypt** data using either the **Caesar cipher** or **Fernet** (from the cryptography library).
- **Decrypt** the data only when the correct passkey is provided 🔓.

### 3. Authentication & Security 🔒
- Allow **three failed attempts** before forcing a reauthorization/login page ⏳.
- Display the **failed attempts count** to notify users about their remaining tries 🚨.

### 4. Streamlit UI (User-Friendly Interface) 🖥️
- **Home Page**: Provides options to store new data or retrieve existing data 🏠.
  
- **Insert Data Page**:
    - User enters the text and a passkey, and the data is stored securely 📥.
  
- **Retrieve Data Page**:
    - User provides a passkey to decrypt the data 🔓.
    - If there are **3 failed attempts**, the user will be redirected to the **Login Page** for reauthorization 🔄.
  
- **Login Page**: A simple login mechanism before the user can retry their actions 🔑.

## 🚀 Additional Challenges

### 1. Data Persistence 💾
- **Store encrypted data** in a **JSON file** instead of in-memory storage.
- Load the data from the file when the app starts up, ensuring persistence across sessions 📂.

### 2. Advanced Security Features 🔐

#### a. Time-Based Lockout ⏰
- Implement a **time-based lockout** mechanism for failed login attempts. 
- After multiple failed attempts, users will be temporarily blocked from retrying 🔒.

#### b. PBKDF2 Hashing for Extra Security 🔑
- Use **PBKDF2 hashing** instead of SHA-256 to add an extra layer of security to the passkeys 🔑.
- PBKDF2 is more resistant to brute-force attacks due to its computationally expensive nature.

### 3. Multi-User System 👥
- Allow **multiple users** to store and retrieve their own data securely.
- Implement a **user authentication system** to manage different user accounts in the Streamlit app 👤.

