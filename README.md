# Deploying Static Website using Load Balancer by ARM Template

## Project Overview

**Develop a dynamic, user-friendly website Restaurant to enhance customer engagement and streamline operations. The site will feature a visually appealing homepage, detailed menu with high-quality images, and an integrated reservation and online ordering system. It will also include an "About Us" page, contact information with Google Maps integration, and links to social media. The website will be responsive, ensuring optimal performance on both desktop and mobile devices. The goal is to effectively represent the restaurant's brand, provide essential information, and improve customer experience.


## Problem Statement

Restaurant faces challenges in reaching and engaging customers effectively due to its outdated and non-responsive website. The current site lacks essential features such as online reservations, menu visibility, and integration with social media, resulting in missed opportunities for customer interaction and streamlined service. To address these issues, the restaurant needs a modern, user-friendly website that provides easy access to the menu, enables online ordering and reservations, and reflects the brand's identity across all devices. This update aims to improve customer satisfaction, drive engagement, and boost overall operational efficiency.


## Project Goals

- Deploy the **Restaurant** website on Azure using ARM templates.
- Set up a **Virtual Network (VNet)** with two **Subnets** and a **Network Security Group (NSG)**.
- Use a **Load Balancer** to distribute traffic between two VMs located in different availability zones.
- Host the static website on these VMs and make it accessible via the load balancer's frontend IP.

## Technologies and Azure Services Used

1. **Azure CLI**: Used to create the resource group and Virtual Network.
2. **ARM Templates**: Automated the creation of VNet, subnets, and NSG.
3. **Azure Virtual Machines (VMs)**: Hosted the Restaurant website.
4. **Azure Load Balancer**: Distributed the traffic between two VMs to ensure high availability.
5. **Nginx**: Used as a web server on both VMs to serve the static content.
6. **Git**: Cloned the website from GitHub onto the VMs using a custom script.
7. **Custom Script Extension**: Used to automatically configure the VMs upon deployment.

## Project Steps

### 1. Website Development
- **Restaurant**: A static website allowing customers to order different variety of dishes within low cost and best quality of hygenic food.

### 2. Deploying the Website on GitHub
- The frontend of **Restaurant** was uploaded to a public GitHub repository: [Frontend-Restaurant](https://github.com/medisettyvaishnavi/Restaurant.git).

### 3. Azure Deployment Using ARM Templates
- **Resource Group**: Created using Azure CLI to hold all the resources.
- **Virtual Network (VNet)**: Set up using an ARM template, which included two subnets for distributing the VMs.
- **Network Security Group (NSG)**: Applied inbound rules to allow traffic on ports 22 (SSH) and 80 (HTTP).
  
### 4. Virtual Machines Setup
- **VM 1**: Created in Availability Zone 1 using Azure Portal. Configured with:
  - Custom Script Extension to clone the website from GitHub.
  - Networking settings to connect to the VNet and assigned Subnet.
  
  Custom Script:
  ```bash
  #!/bin/bash
  sudo apt update
  sudo apt install nginx git -y
  cd /tmp && git clone https://github.com/medisettyvaishnavi/Restaurant.git
  sudo rm -rf /var/www/html/index.nginx-debian.html
  sudo cp -r /tmp/mysitee/* /var/www/html/
  ```

- **VM 2**: Created in Availability Zone 2 with the same configuration as VM 1.

### 5. Load Balancer Configuration
- **Load Balancer**: Configured to distribute traffic between VM 1 and VM 2.
  - **Frontend IP Configuration**: Assigned a new frontend IP for external access.
  - **Backend Pool**: Added both VMs to the backend pool for traffic distribution.
  - **Load Balancing Rule**: Defined to balance HTTP traffic (port 80) across the VMs.
  - **Health Probe**: Set up to monitor the health of the VMs and ensure traffic is routed only to healthy VMs.

### 6. Testing and Accessing the Website
- After the load balancer deployment, the website became accessible via the frontend IP of the load balancer. Customers can access the website **Restaurant** and order the mouth-watering food items.
## How to Use Restaurant

1. Exlpore our website.
2. Select the food item which you want from the menu.
3. Confirm your order by doing payment.
4. If you are satisfied with our service can follow us.

## Azure Services and Tools Used

- **Azure CLI**: Resource group creation and management.
- **Azure Resource Manager (ARM) Templates**: Infrastructure-as-Code to deploy resources.
- **Virtual Network (VNet)**: Networking and subnetting.
- **Network Security Group (NSG)**: Security rules for VM access.
- **Azure Virtual Machines**: Hosting the website on multiple VMs.
- **Azure Load Balancer**: Load balancing between VMs.
- **Nginx**: Web server for hosting static content.
- **Git**: Version control and cloning the website onto VMs.
- **Custom Script Extension**: Automated configuration of VMs.

## Live Website and Resources

- **Website Link**: [Closet.AI](https://github.com/medisettyvaishnavi/Restaurant.git)
- **Project Video**: [Project Video](https://drive.google.com/file/d/1RSElw9IsqCSFR2RPHLPTJIvSfq79zIL1/view?usp=sharing)
- **Screenshots**:
  **Created Resource Group Screenshot**
  - ![ResourceGroup Screenshot](./ARMproject/resourcegroupcreation.png)
    
  **ResourceGroup Deployment Command Output**
  - ![RSG-Deployment-output Screenshot](./ARMproject/deployment_output_1.png)

  **VNet Subnets RSG ARM Template Output**
  - ![VNetDeploymentoutputSS Screenshot](./ARMproject/sub_net.png)

   **Created VNet Screenshot** 
  - ![VNetSS Screenshot](./ARMproject/v_net_ss.png)

  **Created Subnets Screenshot**
  - ![SubnetSS Screenshot](./ARMproject/sub_net.png)

   **Deployed VM 1 Screenshot**
  - ![VM1SS Screenshot](./ARMproject/vm_1.png)

  **Deployed VM 2 Screenshot**
  - ![VM2SS Screenshot](./ARMproject/vm_2.png)

  **Deployed LoadBalancer Screenshot**
  - ![LoadbalancerSS Screenshot](./ARMproject/load_balancer.png)

  **Website Home Page Screenshot**
  - ![RestaurantHomepage Screenshot](./ARMproject/home_page.png)
 
  **Why Choose Us Page after complete Deployment**
  - ![WhyChooseUsPage Screenshot](./ARMproject/why_choose_us.png)

  **Explore Menu Page after complete Deployment**
  - ![ExploreMenuPage Screenshot](./ARMproject/explore_menu.png)

  **Delivery and Follow Page after complete Deployment**
  - ![DeliveryandFollow Screenshot](./ARMproject/follow_us.png)



## Conclusion

This sample business plan provides a comprehensive roadmap for launching and operating a successful **Restaurant**. By following the outlined steps and utilizing the provided resources, entrepreneurs can create a strong foundation for their business and achieve long-term success.


## Author

**B.Vaishnavi**
**Momina Fathima**
**M.Vaishnavi**
Deployed with team as part of learning Azure's cloud infrastructure.
