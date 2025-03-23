# **EC2-AUTOMATION-WITH-TERRAFORM**

This README provides detailed steps on how to set up and automate the **EC2 Instance** using **Terraform**.

---

## **1. Install Terraform**

- Download Terraform from their website [Terraform Download](https://www.terraform.io/).
- Verify installation:
```bash
terraform -v
```

![t1](https://github.com/user-attachments/assets/7d976f3d-ba86-40bb-8c44-5313d6cf3887)


---

## **2. Configure AWS Credentials**

- Terraform needs access to AWS. Setup your credentials using:
```bash
aws configure
```

![t2](https://github.com/user-attachments/assets/ec74152a-4c6c-4d6b-b0bc-767fb7029dcc)



---

## **3. Create a Terraform Configuration File**

- Create a new directory for your Terraform project and create a file named main.tf.
```bash
mkdir terraform-ec2 && cd terraform-ec2
touch main.tf
```

![t3](https://github.com/user-attachments/assets/f8824e2e-bf94-4493-9ad0-ea5d8049f513)



---

## **4. Write Terraform Configuration for EC2**

- Edit main.tf and add the following configuration:
```bash
provider "aws" {
  region = "us-east-1"  # Change to your preferred region
}

resource "aws_instance" "example" {
  ami           = "ami-0c55b159cbfafe1f0"  # Amazon Linux AMI (Check for your region)
  instance_type = "t2.micro"

  tags = {
    Name = "MyTerraformInstance"
  }
}
```

![4](https://github.com/user-attachments/assets/67d56f09-7625-49a4-acb4-25e790e0f78e)

---

## **5. Initialize Terraform**

- Run the following command to initialize Terraform:
```bash
terraform init
```

![t4](https://github.com/user-attachments/assets/789dd550-8653-479b-974d-4a5fb878c4fa)



---

## **6. Validate and Plan**

- heck for syntax errors and see what Terraform will create:
```bash
terraform validate
terraform plan
```

![t5](https://github.com/user-attachments/assets/4ea39e99-5a88-410a-9aae-ed6e3bd1c5f0)



---

## **7. Apply the Configuration**

- To create the EC2 instance, run:
```bash
terraform apply -auto-approve
```

![t6](https://github.com/user-attachments/assets/7a5b3823-c962-4e65-8cf6-c35c27aed49d)

[8](https://github.com/user-attachments/assets/382bdb26-76ae-424c-8ba4-10d77f817786)

---

## **8. Verify the Instance**

- Once the instance is created, you can verify it:
```bash
aws ec2 describe-instances --query 'Reservations[*].Instances[*].[InstanceId,State.Name,PublicIpAddress]' --output table
```

![t7](https://github.com/user-attachments/assets/2dfef70e-3160-41d7-a3b6-b1958e56ea63)



- Or check in the AWS Console.
![terr](https://github.com/user-attachments/assets/74fbdfc2-05dd-4907-b0f3-7df6db60b23e)



---

## **9. Destroy the Instance**

- If you want to delete the EC2 instance, run:
```bash
terraform destroy -auto-approve
```

![t8](https://github.com/user-attachments/assets/eb95106e-bc85-4701-94b7-e11775321f62)

[12](https://github.com/user-attachments/assets/1e670c1e-c003-47b5-a173-e62ed99381e9)

---

## **10. Conclusion**

- You now have automated your EC2 instance using Terraform. With this you can create/destroy any instance you want to without opening the AWS console.
- For more advanced configurations, refer to the [Devstack Documentation](https://github.com/openstack/devstack)
