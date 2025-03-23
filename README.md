# **EC2-AUTOMATION-WITH-TERRAFORM**

This README provides detailed steps on how to set up and automate the **EC2 Instance** using **Terraform**.

---

## **1. Install Terraform**

- Download Terraform from their website [Terraform Download](https://www.terraform.io/).
- Verify installation:
```bash
terraform -v
```

![1]![t1](https://github.com/user-attachments/assets/4d346c04-9298-481f-91c8-7a237f8befe3)

---

## **2. Configure AWS Credentials**

- Terraform needs access to AWS. Setup your credentials using:
```bash
aws configure
```

![2]![t2](https://github.com/user-attachments/assets/cbafe3f4-2902-43e5-aa7a-d4a0761ce144)


---

## **3. Create a Terraform Configuration File**

- Create a new directory for your Terraform project and create a file named main.tf.
```bash
mkdir terraform-ec2 && cd terraform-ec2
touch main.tf
```

![3]![t3](https://github.com/user-attachments/assets/124d8227-01dc-4c91-886e-33d41c8f32f6)


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

![5]![t4](https://github.com/user-attachments/assets/d5c34a52-96a3-43e0-a9af-2db3fe1ceba5)


---

## **6. Validate and Plan**

- heck for syntax errors and see what Terraform will create:
```bash
terraform validate
terraform plan
```

![6]![t5](https://github.com/user-attachments/assets/4a653e6a-c804-4851-97f0-4991d70e9f88)


---

## **7. Apply the Configuration**

- To create the EC2 instance, run:
```bash
terraform apply -auto-approve
```

![7]![t6](https://github.com/user-attachments/assets/235c8236-808b-48fa-b768-212625e444bd)
![8](https://github.com/user-attachments/assets/382bdb26-76ae-424c-8ba4-10d77f817786)

---

## **8. Verify the Instance**

- Once the instance is created, you can verify it:
```bash
aws ec2 describe-instances --query 'Reservations[*].Instances[*].[InstanceId,State.Name,PublicIpAddress]' --output table
```

![9]![t7](https://github.com/user-attachments/assets/95371bd9-ee73-46bf-a24a-836d47916653)


- Or check in the AWS Console.

![10]![terr](https://github.com/user-attachments/assets/70b687bc-0a65-46dd-be5b-426662b2f1a5)


---

## **9. Destroy the Instance**

- If you want to delete the EC2 instance, run:
```bash
terraform destroy -auto-approve
```

![11]![t8](https://github.com/user-attachments/assets/10a6dd45-ebce-4a26-bc02-e2a3327ce4fc)
![12](https://github.com/user-attachments/assets/1e670c1e-c003-47b5-a173-e62ed99381e9)

---

## **10. Conclusion**

- You now have automated your EC2 instance using Terraform. With this you can create/destroy any instance you want to without opening the AWS console.
- For more advanced configurations, refer to the [Devstack Documentation](https://github.com/openstack/devstack)
