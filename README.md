# Node.js & Vue.js File Upload to AWS S3

This project demonstrates how to upload files to an AWS S3 bucket using a Node.js backend and a Vue.js frontend.

## Prerequisites

- Node.js (https://nodejs.org/)
- AWS account with an S3 bucket
- Vue CLI (https://cli.vuejs.org/)

## Getting Started

### Clone the Repository

```bash
git clone https://github.com/your-username/your-repository.git
cd your-repository
Backend Setup
Navigate to the backend directory:

```bash

cd backend
Install backend dependencies:

```bash

npm install
Create a .env file in the backend directory based on .env.example:

```bash

cp .env.example .env
Fill in the .env file with your AWS credentials and S3 bucket details:


AWS_ACCESS_KEY_ID=your-access-key-id
AWS_SECRET_ACCESS_KEY=your-secret-access-key
AWS_REGION=your-aws-region
S3_BUCKET_NAME=your-bucket-name
Start the backend server:

```bash
node upload.js
The backend server will start on http://localhost:3000.

Frontend Setup
Navigate to the frontend directory:

```bash
cd ../frontend
Install frontend dependencies:

```bash
npm install
Start the frontend development server:

```bash
npm run serve
The frontend server will start on http://localhost:8080.

Testing the Upload
Open your browser and navigate to http://localhost:8080.
Use the file upload form to select a file and upload it.
The file will be uploaded to your configured S3 bucket.# node-vue-s3-upload
