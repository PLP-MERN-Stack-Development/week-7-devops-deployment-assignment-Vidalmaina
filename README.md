cd frontend
npm run build
REACT_APP_API_URL=https://your-backend-url.com
REACT_APP_API_URL=https://your-backend-url.com
PORT=5000
MONGO_URI=mongodb+srv://<username>:<password>@cluster0.mongodb.net/dbname
mongoose.connect(process.env.MONGO_URI, { 
  useNewUrlParser: true, 
  useUnifiedTopology: true, 
  poolSize: 10 
});
name: CI/CD

on:
  push:
    branches: [main]

jobs:
  build:
    runs-on: ubuntu-latest

    steps:
      - uses: actions/checkout@v3
      - name: Setup Node.js
        uses: actions/setup-node@v3
        with:
          node-version: 18
      - run: npm install
      - run: npm test
      - run: npm run build --prefix frontend
      - run: echo "Deployment step here (Vercel CLI / Render auto-deploy)"
git add .
git commit -m "Deploy MERN app with CI/CD and monitoring"
git push origin main
