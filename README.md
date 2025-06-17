# 🚦 AWS Green-Blue Deployment (Blue-Green Deployment) Lab

> **A hands-on, step-by-step guide for learning and practicing Blue-Green Deployments on AWS EC2 with CodeDeploy!**

---

## 🌱 What is Blue-Green Deployment?

Blue-Green Deployment is a release management strategy that reduces downtime and risk by running two identical production environments (Blue and Green).  
At any time, only one of the environments is live.  
You deploy your new version to the idle environment, test it, and then switch traffic with minimal impact.

---

## 🚀 What You’ll Learn

- How to automate Blue-Green Deployments on AWS EC2
- Using AWS CodeDeploy for seamless application switches
- Writing user-data scripts to bootstrap EC2 instances
- Managing deployment lifecycle with hooks (`beforeInstall`, `applicationStart`)
- Real-world YAMLs: `appspec.yml` for CodeDeploy
- How to validate deployments with custom scripts

---

## 📦 Repository Structure

```plaintext
README.md              # This guide
user-data.txt          # Complete EC2 user-data bootstrap script (Apache + CodeDeploy Agent)
appspec.yml            # CodeDeploy specification for deployment hooks
beforeInstall.sh       # Example: script for pre-deployment actions
applicationStart.sh    # Example: script for app start actions
index.html             # Sample web page (Hello World)
```

---

## 🛠️ Step-by-Step Learning

### 1. **Launch EC2 Instance with User Data**

Use the provided [`user-data.txt`](user-data.txt) script to:

- Install Apache web server
- Set up a "Hello World" web page
- Detect Linux OS type (Amazon/Ubuntu)
- Install AWS CLI, Ruby, jq
- Bootstrap the AWS CodeDeploy Agent for your region

```bash
# In AWS EC2 Launch Wizard, paste the content of user-data.txt under "User data"
```

---

### 2. **Review & Customize CodeDeploy AppSpec**

- Explore [`appspec.yml`](appspec.yml) for defining deployment hooks
- Hook scripts: `beforeInstall.sh` and `applicationStart.sh`  
  _You can add your own verification or cleanup steps!_

---

### 3. **Test Green-Blue Deployment**

1. **Push a change** to `index.html`
2. **Trigger a deployment** using AWS CodeDeploy Console or CLI
3. **Observe** how CodeDeploy uses your scripts and specs to switch traffic with zero downtime!

---

### 4. **Experiment & Extend**

- Try breaking the deployment to observe rollback
- Add app health checks in your scripts
- Practice with multiple EC2 instances for a more realistic scenario

---

## 👩‍💻 Example: Custom user-data Script

```bash
#!/bin/bash -xe
yum update -y
yum install httpd -y
echo 'Hello' >> /var/www/html/index.html
systemctl restart httpd
# ...and more (see user-data.txt for full script)
```
_Full script: [`user-data.txt`](user-data.txt)_

---

## 🎓 Who Is This For?

- DevOps learners aiming to master AWS deployment strategies
- Students prepping for AWS/DevOps interviews
- Anyone wanting to try safe, zero-downtime deployments

---

## 🙋‍♂️ Maintained by Saifee Zibrahim

If you found this repo helpful, ⭐ star it or share to help more learners!  
Feel free to connect or contribute on GitHub.

---

## 📄 License

MIT — Free for personal and educational use.

---

> **Keep deploying safely — automate, test and learn!**
