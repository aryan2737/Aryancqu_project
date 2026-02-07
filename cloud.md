# Cloud Services

[Cloud VM Provider Comparison](#cloud-vm-provider-comparison) | [Total Cost](#total-cost-of-cloud-vms) | [Plan](./plan.md) | [Network Design](./network.md) | [Security](./security.md) | [Ethics](./ethics.md) | [Reflection](./reflection.md) | [Return to index](./README.md)

## Cloud VM Provider Comparison

At the present time, Truelec is operating from their on-site infrastructure, but their hardware has become obsolete and can no longer support their business. As a business solution, Truelec is aiming to migrate to cloud platforms such as Amazon Web Services (AWS) and Microsoft Azure to support their business operations. However, the organization is unsure about which cloud provider to choose, and to determine the most suitable option, a cost comparison will be conducted. To ensure a fair comparison, the default configuration used for AWS and Azure is given below.

1. **Region:** Sydney area to minimize latency and remain compliant with data regulation laws  
2. **Operating System:** Linux-based architecture with Ubuntu operating system  
3. **Processing Power:** 4 vCPUs with approximately 16 GB of RAM  
4. **Storage:** SSD (Solid State Drive) with 500 GB capacity  

For the specifications provided, the cost is calculated for both AWS and Azure, which can be accessed below:

- [AWS](./cloud1-estimate-aws.csv)  
- [Azure](./cloud2-estimate-azure.xlsx)

### Cost of Single VM

- **AWS EC2:** USD 182.55 per month (≈ AUD 261.05)  
- **Microsoft Azure VM:** AUD 244.45 per month  

Microsoft Azure provides a slightly lower monthly operating cost for equivalent specifications.

### Recommended Provider

The cost analysis conducted among both providers shows that **Microsoft Azure** is the most appropriate and cost-effective option for the Truelec organization. The recommendation considers not only short-term expenses but also long-term (5 to 10 years) operational costs, which remain lower compared to AWS. Additionally, Azure offers stronger integration with on-site Microsoft products such as Office, Windows Servers, and Active Directory.

---

## Total Cost of Cloud VMs

If the cost is calculated for five years, the estimated expenses are as follows:

### AWS

- Monthly cost for 7 servers = 261.05 × 7 = **AUD 1,827.35**  
- Annual cost = 1,827.35 × 12 = **AUD 21,928.20**  
- 5-year cost = **AUD 109,641**

### Azure

- Monthly cost for 7 servers = 244.45 × 7 = **AUD 1,711.15**  
- Annual cost = 1,711.15 × 12 = **AUD 20,533.80**  
- 5-year cost = **AUD 102,669**

---

### Cloud Servers vs New Physical Servers

Using cloud virtual machines removes the need for upfront hardware investment, enabling high scalability and reduced maintenance requirements. Other advantages of cloud servers include improved security features, auto-scaling, reliability, redundancy, virtual networking, and dedicated storage services. However, cloud computing also has some disadvantages, such as ongoing operational costs, reliance on internet connectivity to access servers, and the possibility of higher costs if usage is not monitored properly.

On the other hand, purchasing new physical servers eliminates vendor lock-in issues and provides full control over hardware resources. However, it also introduces disadvantages, including higher long-term costs, the need for dedicated management teams, and reduced scalability compared to cloud-based infrastructure.