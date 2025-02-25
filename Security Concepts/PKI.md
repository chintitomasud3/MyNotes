# Public Key Infrastructure (PKI) - Explanation for an Interview  

## **Definition**  
Public Key Infrastructure (PKI) is a system of **policies, procedures, technologies, and roles** that enable **secure digital communications** through **encryption and authentication**. It uses **asymmetric cryptography**, where a **pair of keys (public and private)** is used to encrypt and decrypt data.  

## **Components of PKI**  

1. **Certificate Authority (CA)** → Issues and verifies digital certificates.  
2. **Registration Authority (RA)** → Acts as an intermediary between users and the CA for identity verification.  
3. **Public & Private Keys** → Used for encryption and decryption.  
4. **Digital Certificates** → Prove the authenticity of a user, website, or entity.  
5. **Certificate Revocation List (CRL)** → Maintains a list of revoked certificates.  

## **How PKI Works**  

1. A user requests a digital certificate from the **CA**.  
2. The **CA verifies** the identity and issues a certificate containing the **public key**.  
3. The user can use this certificate to **encrypt messages** or **authenticate securely**.  
4. The recipient verifies the certificate using the **CA's trusted root certificate**.  

## **Use Cases of PKI**  

- **SSL/TLS (HTTPS)** → Secure web browsing.  
- **Email Security** → Encrypts emails using **S/MIME** or **PGP**.  
- **Digital Signatures** → Ensures document integrity.  
- **Two-Factor Authentication (2FA)** → Smart cards, tokens.  

## **Explaining PKI to a Non-Tech Person**  

Imagine you want to send a locked box (**your message**) to a friend. But only your friend should be able to open it.  

- **Public Key** → It's like a **padlock** that your friend shares with everyone. You put your message in the box and lock it with this padlock.  
- **Private Key** → Only your friend has the **key** to open the locked box. No one else can open it.  
- **Certificate Authority (CA)** → Acts like a **trusted authority** that verifies the identity of your friend and confirms that the padlock is genuine.  

Thus, **PKI ensures** that messages are **locked securely**, and only the **intended person can unlock them**, preventing **eavesdropping** or **identity fraud**.  
