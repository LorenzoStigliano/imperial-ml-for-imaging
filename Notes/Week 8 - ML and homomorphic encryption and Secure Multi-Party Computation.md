
## Homomorphic Encryption

- Based on the assumption that one can perform (basic) arithmetic on encrypted values, i.e. addition and multiplication on encrypted values![[Screenshot 2023-02-21 at 17.13.49.png]]
- Standard client server setting, notice bob has access to the data![[Screenshot 2023-02-21 at 17.15.32.png]]
- With public key encryption scheme, but bob still sees data![[Screenshot 2023-02-21 at 17.16.07.png]]
- Homomorphic Encryption, only Alice sees the data![[Screenshot 2023-02-21 at 17.16.49.png]]

### ML and homomorphic encryption
- We need to be able to train the model in homomorphic form 
- Outsourced computation 
- Private prediction 
- Private training

Advantages 
- Can perform inference on encrypted data, i.e. model owner never sees the client’s private data 
- Does not require interaction between data and model owners 
Disadvantages 
- Computationally expensive as it introduces a significant overhead 
- Restricted to certain operations (also because of efficiency concerns)

## Secure Multi-Party Computation

- Confidentiality: neither knows the real value 
- Shared Governance: The value can only be disclosed if everyone agrees![[Screenshot 2023-02-21 at 17.20.21.png]]
- Split the data to parties so the outsourced values are not useful on their own ![[Screenshot 2023-02-21 at 17.20.53.png]]
- Client do the operation and then the can join the result afterwards![[Screenshot 2023-02-21 at 17.21.29.png]]
- Compute average grade (more complex operation)![[Screenshot 2023-02-21 at 17.22.02.png]]
- No one knows the others score, no one knows the other people grades

## Trusted Execution Environments

- Set of CPU instructions to create enclaves in RAM, that no one can access - except code from the enclave itself
- Ensures total confidentiality of data during computation - decryption happens only inside the enclave