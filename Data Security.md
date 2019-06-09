# Keeping The Data Safe

When talking about keeping the data safe it is important to understand the different methods and technologies used. There are different approaches and different methods. This article focuses on two methods anonymization and pseudonymization, which is also highly reccommended by regulations such as GDPR and PCI DSS. 

## What is  anonymized and pseudonymized data?
The legal distinction between anonymized and pseudonymized data is derived from the categorization of  personal data within the regulation, but in general terms it is understood as either re-identifiable or not. Pseudonymous data is reversible and therefore allows for some form of re-identification, while anonymous data is irreversible and cannot be re-identified. Take an example of musicians and their work. Given 15 songs made by author who is marked "Anonymous", the identity of this author is unknown. In given example it is even not know how many authors made these 15 songs, as some might have made 2 or maybe they are all made by one musician. That would be a simple example of anonymization. When a musician is issuing songs under a different name e.g. Stevie Wonder, who is actually named Stevland Hardaway Morris, this would be pseudonymization. With psuedonymization we would know how many different musician contributed. 

With pseudonymized data, we do not know the identify of the musician, but we can understand which entries are the same (given example songs by the same author). Rows 2 & 5 refer to the same author and rows 3 & 6 refer to the same author. The data is typically re-identifable by the usage of a token and a token lookup table. With that additional information we could re-identify Saraha from TijfdSs.

Yet there is also a different between direct and indirect re-identification. 
### Direct identifiers. 
These are variables that point explicitly to particular individuals or units. Examples include:
- Names
- Addresses, including ZIP and other postal codes
- Telephone numbers, including area codes
- Social Security numbers
- Other linkable numbers such as driver's license numbers, certification numbers, etc.

### Indirect identifiers. 
These are variables that can be problematic as they may be used together or in conjunction with other information to identify individual respondents. Examples include:
- Detailed geographic information (e.g., state, county, province, or census tract of residence)
- Organizations to which the respondent belongs
- Educational institutions from which the respondent graduated and year of graduation
- Detailed occupational titles
- Place where respondent grew up
- Exact dates of events (e.g., birth, death, marriage, divorce)
- Detailed income
- Offices or posts held by respondent

This becomes apparent and problematic with anonymization. Returning to my simple example, in case our musician has a certain style that he/she prefers or the instrument sounds, etc. This could allow the listener on basis of analysis to identify the anonymous song's author. Even if it is not the real name, this is still a major concern. 

The indirect identifiers are extremely use-case specific and depend on the data available. But as humans to a large extent are prone to having patterns in their life, a complex analysis of the behavioural patterns, e.g. data with credit card purchases, might allow easy identification of a person. And if this is possible, the data has not been anonymized. 


## Technologies Used
There are many ways to pseudonymize and anonymize the data. Some of which are found below:

### Scrambling

** Scrambling ** is considered irreversible and permanent, to replace the original phrase/word with a new value (usually works as a random selection from the lookup table). It can be considered as permanent data masking.  For example a name "Sarah" could become "Uomol" as the character values match in the lookup table to the new ones. E.g. S -> U.

### Masking

**Masking** allows the full or a part of the data to be hidden with random a new value. I think one of the best examples of the usage comes from display and sending card information. Typical credit card number"5500 0000 0000 0004" will be stored as "XXXX XXXX XXXX 0004". Data masking does not encrypt information. The advantage of masking is the ability to identify data without manipulating actual identities.

### Encryption

**Encryption** renders the original data to unintelligible and the process cannot be reversed without access to the correct decryption key. Encrypted data is commonly referred to as ciphertext, while unencrypted data is called plaintext. The GDPR requires for the additional information (such as the decryption key) to be kept separately from the pseudonymized data.
Encryption works as a relatively simple concept. Data (plaintext) is encrypted with an encryption algorithm and an encryption key. The result of encryption is encrypted data (ciphertext). Ciphertext can only be reversed  if it is decrypted with the correct key. While the concept is simple, it can be made more sophisticated.
Encryption is divided into 2 types:
- Symmetric key
- Asymmetric key

A symmetric key, implies that only one key, to both encode and decode the information, is used. Typically used in one to one sharing and smaller data sets. Symmetric-key encryption is faster than asymmetric encryption, as the sender must exchange the encryption key with the recipient before decryption. Yet in case of a lot of data it becomes hard to manage and store the keys securly. 
Asymmetric, implies that two linked keys, one private and one public, are being used. The encryption key is public and can be used by anyone to encrypt. The widely used Rivest-Sharmir-Adleman (RSA) algorithm is a cryptosystem for public-key encryption. This asymmetry is based on the practical difficulty of the factorization of the product of two large prime numbers. The private key is used to decrypt the data. A really good article about RSA can be found here: https://hackernoon.com/how-does-rsa-work-f44918df914b

### Tokenization

**Tokenization** is a non-mathematical approach to protecting data at rest that replaces sensitive data with non-sensitive substitutes, referred to as tokens. The tokens have no extrinsic or exploitable meaning or value. Tokenization does not alter the type or length of data, which means it can be processed by legacy systems such as databases that may be sensitive to data length and type. 

#### Token Generation
A token can be generated by many ways:
- A mathematically reversible cryptographic function.
- A one-way non-reversible cryptographic function like a hash function with strong, secret salt.
- Assignment through an index function, sequence number or a randomly generated number, which should not be derived from the data.

#### Token Mapping
Token mapping is a process where the data gets assigned to a specific token. When data is submitted for tokenization, the token will be generated and the original data stored in the vault. Token mapping is required to reverse the tokenized data.

#### Vault
In a tokenization system, the data vault is the central repository for data and tokens and is used by the token-mapping process. 

#### Cryptographic Key Management
Cryptographic key management defines the processes for creating, using, managing, and protecting cryptographic keys used for the protection of the data.

### Data blurring

**Data blurring** is a method used most commonly to protect image data. It is based on the approximation of data values which in turn makes it impossible to identify parts of the image. This can be seen in the news articles pictures, where faces are blurred as court trials have not ended.
