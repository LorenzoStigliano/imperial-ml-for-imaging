- Seven key requirements for trustworthy AI/ML
	- Accountability
	- Societal and Environmental well-being
	- Diversity
	- Transparency
	- Privacy and Data Governance
	- Human agency and oversight
	- Technical robustness and safeness

## Privacy and Data Governance

- The power and effectiveness of ML is critically dependent on the data that is used to train our ML models. 
	- Quality of the data is one of the important aspects that determines the effectiveness of ML models: 
		- Curation of the data (and the associated annotations) 
		- Representativeness of the data 
	- Quantity of data
- In general, the more data is available for training, the more accurate and robust the resulting ML models become.
	- Data sharing is more important

### What are the hurdles to getting more data?

- Human and societal challenges
	- Cost and effort for collecting and annotating data 
	- Incentives for data sharing (money, fame, other benefits) 
- Technical challenges 
	- Data quality 
	- Data annotation 
	- Data exchange formats 
- Legal challenges 
	- What is allowed? What consent is required? 
	- Regulation (e.g. GDPR) 
- Privacy challenges 
	- Ethical 
	- Trust (risks such as privacy breaches, data leaks and re-identification)

### Secure and privacy-preserving ML

- Optimal privacy preservation requires implementations that are secure by default so-called privacy by design
- Requirements: 
	- Minimal or no data transfer 
		- Federated learning: train a ML model across decentralised clients with local data, without exchanging them
	- Provision of theoretical and/or technical guarantees of privacy
		- Differential privacy: perturb the data so that information about the single individual is reduced while retaining the capability of learning
- Other approaches for privacy-preserving AI:
	- Homomorphic encryption which enables learning from encrypted data 
	- Secure multi-party computing where processing is performed on encrypted data shares, split among them in a way that no single party can retrieve the entire data on their own. 
	- Trusted execution environments

### Federated learning
- Iterative framework, where the model owner send to the client for training on local data
- Local model updates encrypted and sent back for aggregation
- Aggregate model sent back to local client and model owner![[Screenshot 2023-02-21 at 11.16.41.png]]

In federated learning: 
- Suppose $N$ training samples are distributed to $k$ clients
- $P_k$ is the set of indices of samples at client $k$, and $n_k =|P_k|$
- The loss is given by, it is a weighted average of the losses over the clients:
![[Screenshot 2023-02-21 at 17.05.55.png]]

### Federated SGD
- It can also aggregate the local parameters instead of the gradients
![[Screenshot 2023-02-21 at 17.07.49.png]]
### Federated Averaging
- We can also allow multiple steps of gradient descent and then synchronise after optimisation
![[Screenshot 2023-02-21 at 17.08.21.png]]

### Challenges for federated learning

- Non-IID data 
	- Training data for a given client is typically site specific, hence the site’s local dataset will not be representative of the distribution of training samples.
- Unbalanced data 
	- Sites may have a lot or little training data, leading to varying amounts of local training data across different sites.
- Massively distributed data 
	- There may be extreme scenarios where each site only has very training samples (in the limiting case one example) 
- Communication costs 
	- Communication between clients and servers occurs communication overheads. The amount of overhead will depend on the number of clients and the frequency of updates from/to server.