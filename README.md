## Project Overview
This system is a secure cloud storage solution designed for forensic data integrity. It ensures that the cloud provider (Firebase) never has access to the raw data or the keys, using a "Zero-Knowledge" architecture.

## Core Features
Hybrid Cryptography: Uses AES-GCM (256-bit) for high-speed file encryption and RSA-OAEP (2048-bit) for secure key wrapping.

Zero-Knowledge Architecture: All encryption/decryption happens client-side in the browser via the Web Crypto API.

Forensic Accountability: Every file generates a SHA-256 hash stored in an immutable audit trail to detect tampering.

PKI Management: Automated Public Key Infrastructure (PKI) using Firestore for secure multi-user file sharing.

## Technology Stack
Frontend: HTML5, CSS3, JavaScript (ES6+).

Security Engine: Web Crypto API (SubtleCrypto).

Backend/Database: Firebase Authentication, Firestore (NoSQL), and Firebase Storage.

## How It Works (The Crypto Flow)
Key Generation: RSA Key Pairs are generated locally. Public keys are sent to Firestore.

Upload: Files are hashed, encrypted with AES, and the AES key is "wrapped" with the user's RSA Public Key.

Download: The RSA Private Key unwraps the AES key to restore the file.

Verification: The system re-hashes the file and compares it to the forensic log to ensure 100% integrity.
