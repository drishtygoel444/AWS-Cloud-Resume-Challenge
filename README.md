# 🚀 AWS Cloud Resume Challenge - Drishty's Portfolio

A complete, production-ready personal portfolio website hosted entirely on AWS, demonstrating hands-on knowledge of multiple AWS services.

## ✨ Live Demo
- **Website**: [Your CloudFront URL will be here after deployment]
- **Architecture**: Multi-tier AWS application with CI/CD pipeline

## 🏗️ Architecture Overview

```
Internet → CloudFront → S3 (Static Website)
                ↓
            API Gateway → Lambda → DynamoDB (Visitor Counter)
                ↓
            CloudWatch (Monitoring & Logs)
```

## 🎯 AWS Services Demonstrated

- **S3** - Static website hosting
- **CloudFront** - Content delivery network with HTTPS
- **API Gateway** - RESTful API endpoints
- **Lambda** - Serverless backend functions (Python)
- **DynamoDB** - NoSQL database for visitor tracking
- **IAM** - Security roles and permissions
- **CloudWatch** - Monitoring and logging
- **CodePipeline** - CI/CD deployment automation

## 📁 Project Structure

```
aws-cloud-resume/
├── frontend/                 # Static website files
│   ├── index.html           # Main portfolio page
│   ├── styles.css           # Styling
│   ├── script.js            # Frontend JavaScript
│   └── assets/              # Images and other assets
├── backend/                  # Lambda functions
│   ├── visitor-counter.py   # Main Lambda function
│   └── requirements.txt     # Python dependencies
├── infrastructure/           # AWS infrastructure code
│   ├── cloudformation.yaml  # Infrastructure as Code
│   └── deploy.sh           # Deployment script
├── docs/                    # Documentation
│   └── architecture.png     # Architecture diagram
└── README.md               # This file
```

## 🚀 Quick Start

### Prerequisites
- AWS CLI configured with appropriate permissions
- Python 3.8+ installed
- Basic knowledge of AWS services

### Deployment Steps

1. **Clone and Setup**
   ```bash
   git clone <your-repo-url>
   cd aws-cloud-resume
   ```

2. **Deploy Infrastructure**
   ```bash
   cd infrastructure
   ./deploy.sh
   ```

3. **Upload Frontend**
   ```bash
   aws s3 sync ../frontend/ s3://your-bucket-name --delete
   ```

4. **Test the Application**
   - Visit your CloudFront distribution URL
   - Check visitor counter functionality
   - Verify CloudWatch logs

## 🔧 Configuration

### Environment Variables
- `DYNAMODB_TABLE`: DynamoDB table name for visitor counter
- `AWS_REGION`: AWS region for deployment

### Customization
- Update `frontend/index.html` with your personal information
- Modify `frontend/styles.css` for custom styling
- Adjust Lambda function logic in `backend/visitor-counter.py`

## 📊 Monitoring & Analytics

- **CloudWatch Logs**: Lambda execution logs
- **CloudWatch Metrics**: API Gateway and Lambda performance
- **DynamoDB Metrics**: Database performance and usage

## 🔒 Security Features

- HTTPS enforced via CloudFront
- IAM roles with least privilege access
- API Gateway authentication (optional)
- S3 bucket policies for secure access

## 🎓 Learning Outcomes

This project demonstrates:
- ✅ Multi-service AWS architecture design
- ✅ Infrastructure as Code (CloudFormation)
- ✅ Serverless application development
- ✅ CI/CD pipeline implementation
- ✅ AWS security best practices
- ✅ Monitoring and logging setup

## 📝 For Cognizant Submission

### What to Include:
1. **GitHub Repository Link** - This complete project
2. **Live Website URL** - Your deployed CloudFront distribution
3. **Architecture Diagram** - Visual representation of the solution
4. **Deployment Instructions** - Step-by-step setup guide
5. **Code Quality** - Clean, well-documented, production-ready code

### Key Benefits:
- **Real AWS Experience**: Uses actual AWS services, not just theory
- **Production Ready**: Follows AWS best practices and security guidelines
- **Scalable**: Architecture can handle production workloads
- **Cost Effective**: Serverless design minimizes operational costs
- **Professional**: Clean code structure suitable for enterprise environments

## 🤝 Contributing

This is a personal portfolio project, but feel free to fork and customize for your own use!

## 📄 License

MIT License - Feel free to use this project for your portfolio and interviews.

---

**Built with ❤️ for AWS Cloud Resume Challenge**
**Ready for Cognizant submission as proof of AWS skills! 🎯** 