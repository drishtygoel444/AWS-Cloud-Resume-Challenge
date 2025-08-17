# 🚀 Deployment Guide - AWS Cloud Resume Challenge

This guide will walk you through deploying your complete AWS Cloud Resume Challenge project step by step.

## 📋 Prerequisites

Before you begin, ensure you have:

- ✅ AWS Account with appropriate permissions
- ✅ AWS CLI installed and configured
- ✅ Python 3.8+ installed
- ✅ Git repository set up
- ✅ Basic knowledge of AWS services

## 🔧 Step 1: AWS CLI Configuration

### Install AWS CLI
```bash
# macOS
brew install awscli

# Windows
# Download from: https://aws.amazon.com/cli/

# Linux
curl "https://awscli.amazonaws.com/awscli-exe-linux-x86_64.zip" -o "awscliv2.zip"
unzip awscliv2.zip
sudo ./aws/install
```

### Configure AWS Credentials
```bash
aws configure
# Enter your AWS Access Key ID
# Enter your AWS Secret Access Key
# Enter your default region (e.g., us-east-1)
# Enter your output format (json)
```

## 🏗️ Step 2: Deploy Infrastructure

### Navigate to Infrastructure Directory
```bash
cd infrastructure
```

### Make Deployment Script Executable
```bash
chmod +x deploy.sh
```

### Run Deployment Script
```bash
./deploy.sh
```

**What this script does:**
1. ✅ Checks AWS CLI installation
2. ✅ Creates Lambda deployment package
3. ✅ Deploys CloudFormation stack
4. ✅ Updates Lambda function code
5. ✅ Deploys website to S3
6. ✅ Shows deployment information

### Expected Output
```
[INFO] Checking AWS CLI installation...
[SUCCESS] AWS CLI is installed
[SUCCESS] AWS credentials are configured
[INFO] Creating Lambda deployment package...
[SUCCESS] Lambda package created successfully
[INFO] Deploying CloudFormation stack: drishty-cloud-resume-production
[INFO] Creating new stack...
[SUCCESS] Stack deployment completed successfully
[INFO] Updating Lambda function code...
[SUCCESS] Lambda function updated successfully
[INFO] Deploying website to S3...
[SUCCESS] Website deployed to S3 successfully
```

## 🌐 Step 3: Update Frontend Configuration

### Get API Endpoint URL
After deployment, you'll see output like:
```
🔌 API Endpoint: https://abc123.execute-api.us-east-1.amazonaws.com/production/visitor-count
```

### Update JavaScript File
Edit `frontend/script.js` and update the API endpoint:

```javascript
// Find this line in the VisitorCounter class
this.apiEndpoint = 'https://your-api-gateway-url.amazonaws.com/visitor-count';

// Replace with your actual API Gateway URL
this.apiEndpoint = 'https://abc123.execute-api.us-east-1.amazonaws.com/production/visitor-count';
```

### Redeploy Website
```bash
cd infrastructure
./deploy.sh
```

## 🧪 Step 4: Test Your Application

### Test Website
1. Visit your CloudFront URL (shown in deployment output)
2. Check if the website loads correctly
3. Verify all sections are visible
4. Test mobile responsiveness

### Test Visitor Counter
1. Refresh the page multiple times
2. Check if visitor count increments
3. Open browser developer tools
4. Look for any JavaScript errors

### Test API Endpoint
```bash
# Test the API directly
curl -X POST https://your-api-url.amazonaws.com/production/visitor-count \
  -H "Content-Type: application/json" \
  -d '{"action": "increment"}'
```

## 📊 Step 5: Monitor and Verify

### Check CloudWatch Dashboard
1. Go to AWS Console → CloudWatch
2. Navigate to Dashboards
3. Find your project dashboard
4. Verify metrics are being collected

### Check Lambda Logs
1. Go to AWS Console → Lambda
2. Select your visitor-counter function
3. Click on "Monitor" tab
4. Check CloudWatch logs

### Check DynamoDB
1. Go to AWS Console → DynamoDB
2. Select your visitor-counter table
3. Verify data is being stored
4. Check item count

## 🔄 Step 6: Customize Your Website

### Update Personal Information
Edit `frontend/index.html`:
- Change name, title, and description
- Update skills and experience
- Modify project descriptions
- Add your contact information

### Customize Styling
Edit `frontend/styles.css`:
- Change color scheme
- Modify fonts and spacing
- Adjust layout and animations
- Add custom CSS

### Update Content
- Replace placeholder text with your information
- Add your own projects
- Include your certifications
- Add your social media links

## 🚀 Step 7: Set Up CI/CD (Optional)

### Option 1: GitHub Actions
Create `.github/workflows/deploy.yml`:

```yaml
name: Deploy to AWS
on:
  push:
    branches: [ main ]
jobs:
  deploy:
    runs-on: ubuntu-latest
    steps:
      - uses: actions/checkout@v2
      - name: Configure AWS credentials
        uses: aws-actions/configure-aws-credentials@v1
        with:
          aws-access-key-id: ${{ secrets.AWS_ACCESS_KEY_ID }}
          aws-secret-access-key: ${{ secrets.AWS_SECRET_ACCESS_KEY }}
          aws-region: us-east-1
      - name: Deploy to S3
        run: |
          aws s3 sync frontend/ s3://your-bucket-name --delete
          aws cloudfront create-invalidation --distribution-id your-distribution-id --paths "/*"
```

### Option 2: AWS CodePipeline
1. Go to AWS Console → CodePipeline
2. Create new pipeline
3. Connect to your Git repository
4. Configure build and deploy stages

## 🔍 Step 8: Troubleshooting

### Common Issues and Solutions

#### Issue: Website not loading
**Solution:**
- Check S3 bucket permissions
- Verify CloudFront distribution status
- Check for CloudFormation stack errors

#### Issue: Visitor counter not working
**Solution:**
- Verify API Gateway URL in JavaScript
- Check Lambda function logs
- Ensure DynamoDB table exists
- Check IAM permissions

#### Issue: Deployment script fails
**Solution:**
- Verify AWS CLI configuration
- Check AWS credentials and permissions
- Ensure all required tools are installed
- Check CloudFormation stack status

#### Issue: High costs
**Solution:**
- Monitor CloudWatch metrics
- Set up billing alerts
- Review resource usage
- Optimize Lambda function

## 📝 Step 9: Documentation for Cognizant

### What to Include in Your Submission

1. **GitHub Repository Link**
   - Complete project with all files
   - Clear README and documentation
   - Working code examples

2. **Live Website URL**
   - Your CloudFront distribution URL
   - Functional visitor counter
   - Professional portfolio design

3. **Architecture Documentation**
   - Architecture diagram (from docs/architecture.md)
   - Service explanations
   - Deployment process

4. **Code Quality**
   - Clean, well-documented code
   - Proper error handling
   - Security best practices

5. **AWS Services Demonstrated**
   - S3, CloudFront, Lambda, DynamoDB
   - API Gateway, CloudWatch, IAM
   - CloudFormation, CodePipeline (optional)

## 🎯 Step 10: Final Verification

### Pre-Submission Checklist

- [ ] Website loads correctly
- [ ] Visitor counter increments
- [ ] All sections display properly
- [ ] Mobile responsive design
- [ ] No JavaScript errors
- [ ] CloudWatch metrics active
- [ ] Lambda function working
- [ ] DynamoDB storing data
- [ ] API Gateway accessible
- [ ] Documentation complete

### Performance Testing

```bash
# Test website performance
curl -w "@curl-format.txt" -o /dev/null -s "https://your-cloudfront-url"

# Test API response time
time curl -X POST https://your-api-url.amazonaws.com/production/visitor-count \
  -H "Content-Type: application/json" \
  -d '{"action": "increment"}'
```

## 🎉 Congratulations!

You've successfully deployed a complete, production-ready AWS Cloud Resume Challenge! This project demonstrates:

- ✅ **Real AWS Experience**: Actual services, not just theory
- ✅ **Production Ready**: Follows AWS best practices
- ✅ **Scalable Architecture**: Can handle production workloads
- ✅ **Cost Effective**: Serverless design minimizes costs
- ✅ **Professional Quality**: Enterprise-grade implementation

## 📞 Need Help?

If you encounter any issues:

1. Check the troubleshooting section above
2. Review CloudFormation stack events
3. Check CloudWatch logs for errors
4. Verify IAM permissions
5. Ensure all services are in the same region

## 🔗 Useful Links

- [AWS CloudFormation Documentation](https://docs.aws.amazon.com/cloudformation/)
- [AWS Lambda Documentation](https://docs.aws.amazon.com/lambda/)
- [AWS S3 Documentation](https://docs.aws.amazon.com/s3/)
- [AWS CloudFront Documentation](https://docs.aws.amazon.com/cloudfront/)

---

**Your AWS Cloud Resume Challenge is ready for Cognizant submission! 🚀** 