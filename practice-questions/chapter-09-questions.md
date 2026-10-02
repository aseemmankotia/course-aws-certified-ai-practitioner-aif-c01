## Chapter 9: Domain 5: Security, Compliance & Governance for AI — Practice Questions

**Q1.** A healthcare company is building a medical records analysis application using Amazon Bedrock. They need to ensure that all patient data stored in S3 and used for model training in SageMaker is encrypted at rest with keys they control and can rotate. Which solution meets these requirements while maintaining compliance?

A) Use AWS-managed encryption keys (SSE-S3) for S3 buckets and default SageMaker encryption
B) Create customer-managed KMS keys (CMK) for S3 bucket encryption and SageMaker notebook volumes, enable automatic key rotation
C) Enable S3 bucket encryption with AES-256 and use EC2 instance store for SageMaker training
D) Use AWS managed KMS keys for both S3 and SageMaker with CloudTrail logging enabled

<details>
<summary>Answer</summary>

**Correct: B**

Customer-managed KMS keys (CMK) give full control over encryption keys including rotation policies, required for healthcare compliance. Costs $1/month per key. Supports both S3 and SageMaker encryption at rest.

**Why the others are wrong:**
- AWS-managed keys don't provide customer control over rotation and key lifecycle, fails compliance requirement for customer-controlled keys
- Instance store is ephemeral and not encrypted by default, AES-256 alone doesn't provide the key management controls required
- AWS managed KMS keys are controlled by AWS, not the customer, failing the 'keys they control' requirement

> ⚠️ Frequently missed on the exam — read the options carefully.

</details>

---

**Q2.** A financial services company needs to invoke multiple foundation models in Amazon Bedrock from their Lambda functions. Security policy requires least privilege access. Which IAM policy configuration is MOST appropriate?

A) Attach AmazonBedrockFullAccess managed policy to the Lambda execution role
B) Create a policy with bedrock:* permissions for all Bedrock resources
C) Create a policy with bedrock:InvokeModel permission restricted to specific model ARNs they use (e.g., arn:aws:bedrock:us-east-1::foundation-model/anthropic.claude-v2)
D) Create a policy with bedrock:InvokeModel and bedrock:GetFoundationModel for all foundation models in the region

<details>
<summary>Answer</summary>

**Correct: C**

Least privilege requires restricting bedrock:InvokeModel to only the specific foundation model ARNs actually used. Exam tests exact permission format and resource-level restrictions.

**Why the others are wrong:**
- AmazonBedrockFullAccess grants excessive permissions including management operations not needed for invoking models
- bedrock:* violates least privilege principle by granting all Bedrock actions including admin operations
- Granting access to all foundation models violates least privilege when only specific models are needed

</details>

---

**Q3.** A company discovers that their S3 bucket containing training data includes customer PII that should not be there. They need an automated solution to continuously scan for sensitive data and alert on findings. Which AWS service BEST meets this requirement?

A) Amazon GuardDuty with S3 protection enabled, $0.50/GB/month for S3 data scanned
B) AWS Config with custom rules to detect PII in S3 object metadata
C) Amazon Macie to perform ML-powered sensitive data discovery, $1/GB scanned, continuous monitoring
D) Amazon Inspector to scan S3 buckets for PII and compliance violations

<details>
<summary>Answer</summary>

**Correct: C**

Macie is specifically designed for discovering and protecting sensitive data in S3 using ML. Costs $1/GB scanned. Exam tests knowing Macie is the PII/sensitive data discovery service.

**Why the others are wrong:**
- GuardDuty detects threats and malicious activity, not PII content within objects. Wrong service for data discovery.
- AWS Config evaluates resource configurations, not object content. Cannot scan inside S3 objects for PII.
- Amazon Inspector scans EC2/containers for vulnerabilities, not S3 content for sensitive data

> ⚠️ Frequently missed on the exam — read the options carefully.

</details>

---

**Q4.** An enterprise requires that all Amazon Bedrock API calls from their VPC never traverse the public internet due to regulatory requirements. They need to invoke the Bedrock Runtime API from EC2 instances. What configuration is required?

A) Create a NAT Gateway and route Bedrock traffic through it with TLS encryption
B) Enable VPC peering between the application VPC and AWS service VPC for Bedrock
C) Create a VPC endpoint for com.amazonaws.region.bedrock-runtime with PrivateLink, update route tables
D) Configure AWS Direct Connect and route Bedrock API calls through the dedicated connection

<details>
<summary>Answer</summary>

**Correct: C**

VPC endpoints for Bedrock Runtime (com.amazonaws.region.bedrock-runtime) use PrivateLink to keep traffic within AWS network. Exam tests exact service endpoint format.

**Why the others are wrong:**
- NAT Gateway still routes traffic over public internet even with TLS, fails the 'never traverse public internet' requirement
- Cannot peer with AWS service VPCs. VPC endpoints/PrivateLink is the correct mechanism for private AWS service access.
- Direct Connect is for on-premises connectivity, overkill and doesn't prevent internet routing from VPC to AWS services

</details>

---

**Q5.** A SageMaker training job processes sensitive financial data. During the job, data is transmitted between S3, training instances, and the SageMaker service. Which encryption approach secures data in transit?

A) Enable S3 bucket encryption with SSE-KMS and SageMaker volume encryption with CMK
B) TLS 1.2+ is automatically enforced for all SageMaker API calls and data transfers between S3 and training instances
C) Configure IPSec VPN tunnels between S3 buckets and SageMaker training instances
D) Use SageMaker network isolation mode and enable VPC encryption

<details>
<summary>Answer</summary>

**Correct: B**

SageMaker automatically encrypts data in transit using TLS 1.2+. Exam tests that encryption in transit is automatic/default for AWS AI services. No manual configuration needed.

**Why the others are wrong:**
- SSE-KMS and volume encryption are for data at rest, not in transit. Wrong encryption type for the requirement.
- Cannot configure IPSec between S3 and SageMaker. TLS is the transport encryption method, not IPSec.
- Network isolation prevents internet access but doesn't encrypt data. VPC encryption is not a feature that exists.

> ⚠️ Frequently missed on the exam — read the options carefully.

</details>

---

**Q6.** A compliance team needs to track all Amazon Bedrock InvokeModel API calls including the model IDs used and request parameters for audit purposes. The logs must be retained for 7 years. Which solution meets these requirements MOST cost-effectively?

A) Enable CloudWatch Logs for Bedrock with 7-year retention, $0.50/GB ingested
B) Enable CloudTrail with data events for Bedrock, store logs in S3 with Glacier Deep Archive storage class after 90 days, $0.025/GB/month for S3 Standard then $0.00099/GB/month for Glacier
C) Enable VPC Flow Logs to capture all Bedrock API traffic and store in S3
D) Configure AWS Audit Manager to automatically collect Bedrock API call evidence

<details>
<summary>Answer</summary>

**Correct: B**

CloudTrail data events log API calls including parameters. S3 storage at $0.025/GB/month (Standard) then transition to Glacier Deep Archive ($0.00099/GB/month) is most cost-effective for 7-year retention. Exam tests CloudTrail for API logging and cost optimization with S3 storage classes.

**Why the others are wrong:**
- CloudWatch Logs at $0.50/GB ingested is 20x more expensive than S3 storage, and less suitable for long-term archive
- VPC Flow Logs capture network traffic metadata, not API call details like model IDs and parameters
- Audit Manager collects evidence but requires CloudTrail as the underlying logging mechanism, adds unnecessary complexity

</details>

---

**Q7.** A company must demonstrate SOC 2 compliance for their AI application using Bedrock and SageMaker. They need automated evidence collection for audits showing encryption, access controls, and monitoring are properly configured. Which service BEST supports this requirement?

A) AWS Security Hub to aggregate security findings from Bedrock and SageMaker
B) AWS Audit Manager with pre-built SOC 2 framework to automatically collect compliance evidence
C) AWS Config to continuously assess Bedrock and SageMaker resource compliance
D) Amazon Detective to investigate and analyze compliance-related security events

<details>
<summary>Answer</summary>

**Correct: B**

Audit Manager has pre-built compliance frameworks (SOC 2, PCI-DSS, etc.) that automate evidence collection from AWS services. Generates audit-ready reports. Exam tests knowing Audit Manager is for compliance automation.

**Why the others are wrong:**
- Security Hub aggregates findings but doesn't provide compliance framework mapping or automated audit reports
- Config assesses compliance but doesn't provide the audit framework structure or automated evidence collection for SOC 2
- Detective is for security investigation and root cause analysis, not compliance evidence collection

> ⚠️ Frequently missed on the exam — read the options carefully.

</details>

---

**Q8.** Under the AWS Shared Responsibility Model, a customer is deploying a Bedrock-based application. Which security tasks are the CUSTOMER's responsibility?

A) Patching the underlying infrastructure running Bedrock foundation models and securing the hypervisor layer
B) Configuring IAM policies for bedrock:InvokeModel permissions, encrypting training data in S3, and managing KMS keys for data encryption
C) Maintaining physical security of data centers and ensuring foundation model availability
D) Securing the Bedrock API endpoints and implementing DDoS protection for AWS infrastructure

<details>
<summary>Answer</summary>

**Correct: B**

Customer responsibility: IAM policies, data encryption, KMS key management. AWS secures infrastructure. Exam heavily tests shared responsibility boundaries for AI services.

**Why the others are wrong:**
- Infrastructure patching and hypervisor security are AWS responsibilities (security OF the cloud)
- Physical security and service availability are AWS responsibilities managed at the infrastructure layer
- API endpoint security and DDoS protection for AWS infrastructure are AWS responsibilities

</details>

---

