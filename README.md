# Cloud Security in Microsoft Azure

# Implementing-Network-Security-Groups-in-Azure

In this write-up, we will walk through my process of setting up a secure cloud environment using Azure by implementing a Virtual Network, deploying a Virtual Machine, and creating and configuring a Network Security Group (NSG) to control traffic access.

## Step 1: Create a Virtual Network
![1](https://github.com/user-attachments/assets/4361068f-3c06-4581-8c83-5021d7f77cba)

A virtual network is the backbone for communicating between various resources in Azure. It provides a secure environment to operate and allows the segmentation of network resources. 

Review the configurations you want to have and create the virtual network.


## Step 2: Launch an Azure Virtual Machine
![2](https://github.com/user-attachments/assets/2201e2f3-9c33-4a42-b7d6-ca249c8e4fb0)


Having established the virtual network, the next step is to deploy a Virtual Machine (VM) that will run your applications.

**Instructions:**

1. In the Azure portal, navigate back to "Create a resource" and select "Virtual Machine."
2. Configure the VM with the following settings:
   - **Name:** 
   - **Region:** Select a region that best fits your needs.
   - **Image:** Windows Server 2019 Datacenter
   - **Size:** B1s (Basic)
   - **Authentication type:** Password
   - **Username:** 
   - **Password:**
3. Connect the VM to the previously created virtual network and the subnet.
4. Review and create the virtual machine.

## Step 3: Create a Network Security Groups (NSGs)
![3](https://github.com/user-attachments/assets/557632f5-630c-4b32-8df6-780250b769bf)


To enhance security and control traffic to and from the VM, we will implement an NSG. An NSG is a set of security rules that allow or deny inbound and outbound traffic based on defined conditions.

**Instructions:**

1. Go to "Create a resource" and select "Network Security Group."
2. Configure the NSG with the following settings:
   - **Name:**
   - **Region:** The same as the VM region to avoid latency issues.
3. Review and create the NSG.

## Step 4: Configure Inbound and Outbound Security Rules
![4](https://github.com/user-attachments/assets/bc3cf07d-49fd-4cdf-9c14-33ff62ff4f9f)

With the NSG in place, it is crucial to define the traffic rules that will govern access to your VM. 

**Instructions:**

1. Navigate to the newly created NSG, 
2. Click on "Inbound security rules" under Settings.
3. Add an inbound rule to allow RDP access:
   - **Source:** IP Addresses
   - **Source IP address:** Your IP address
   - **Destination:** Any
   - **Destination port ranges:** 3389
   - **Protocol:** TCP
   - **Action:** Allow
   - **Priority:** 1000
   - **Name:** Allow-RDP
4. Under "Settings," select "Outbound security rules" and ensure that the default outbound rule allows all outbound traffic.

## Step 5: Associate NSG with the VM's Network Interface
![5](https://github.com/user-attachments/assets/dcbd788f-9ba6-4372-a321-7cbb22d19ca9)

To enforce the security rules created in the NSG, you must associate the NSG with the network interface of the VM.

**Instructions:**

1. Navigate to the VM in the Azure portal.
2. Under the networking section, find the network interface associated with your VM.
3. Select the option to associate an NSG and choose the NSG we created



## Conclusion
![6](https://github.com/user-attachments/assets/a9ed9880-6b48-47f5-ae7a-5440abcb2e0d)

By following these steps, you have successfully set up a secure cloud environment in Azure with a virtual network, deployed a virtual machine, and created and configured a network security group. Each element plays a crucial role in safeguarding your resources and controlling traffic flow, demonstrating best practices in cloud security. This setup ensures that only authorized users can access the VM while allowing the necessary outbound connectivity for operations.
