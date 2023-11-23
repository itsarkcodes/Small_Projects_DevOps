# Access Grafana dashboard 
Access the Instance:- http://35.170.229.118:3000/   
Username: ```admin```   
Password: ```password```
<hr/>

# Setting Up Grafana on AWS EC2

These are all the steps to set up Grafana on an AWS EC2 instance.

## Overview
Grafana is an open-source platform for monitoring and observability, allowing you to create dashboards and visualize data from various sources.

## Installation Steps

1. **Launch EC2 Instance**
   - Launch an EC2 instance using your preferred Linux distribution (Ubuntu recommended).
   
2. **Connect to EC2 Instance**
   - Connect to your EC2 instance via SSH:
     ```bash
     ssh -i /path/to/your-key.pem ec2-user@your-ec2-instance-ip
     ```

3. **Install Grafana**
   - Update package lists:
     ```bash
     sudo apt update
     ```
   - Install Grafana:
     ```bash

     sudo apt install -y software-properties-common wget
     wget -q -O - https://packages.grafana.com/gpg.key | sudo apt-key add -
     sudo add-apt-repository "deb https://packages.grafana.com/oss/deb stable main"
     sudo apt update
     sudo apt install grafana
     ```
   
4. **Start and Enable Grafana**
   - Start Grafana service:
     ```bash
     sudo systemctl start grafana-server
     ```
   - Enable Grafana service to start on boot:
     ```bash
     sudo systemctl enable grafana-server
     ```

5. **Access Grafana**
   - Open a web browser and enter your EC2 instance's public IP address followed by port 3000:
     ```
     http://your-ec2-instance-ip:3000
     ```
   - Login to Grafana using the default credentials:
     - Username: `admin`
     - Password: `admin` 

6. **Configure Grafana**
   - Follow the on-screen prompts to set up data sources, create dashboards, and configure Grafana according to your monitoring needs.

## Additional Resources

- [Grafana Documentation](https://grafana.com/docs/grafana/latest/)
- [AWS EC2 Documentation](https://docs.aws.amazon.com/ec2/)
- [Grafana Community](https://community.grafana.com/)

## License

This project is licensed under the [MIT License](LICENSE).
