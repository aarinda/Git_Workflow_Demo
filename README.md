# Git_Workflow_Demo

This GitHub Actions workflow is designed to automate the process of deploying a static website to GitHub Pages whenever changes are pushed to the `main` branch of your repository. The workflow does the following:

1. **Trigger:** The workflow is triggered on every push event to the `main` branch.

2. **Environment:** It runs on the latest version of Ubuntu.

3. **Steps:**

   - **Checkout code:** It checks out the code from the repository using the `actions/checkout` action.

   - **Build and Deploy:** The code is copied and prepared for deployment in the `public` directory. It creates an `index.html` file and a `deployed.txt` file in the `public` directory.

   - **Deploy to GitHub Pages:** The final step uses the `peaceiris/actions-gh-pages` action to deploy the contents of the `public` directory to the GitHub Pages branch. The following parameters are configured for this step:
     - `github_token`: This is a GitHub token stored as a secret (`Workflow_Token`) in your repository. It is used for authentication when pushing the changes to the GitHub Pages branch.
     - `publish_dir`: This specifies the directory to be published, which is set to `./public`. This directory is the one where the website content is prepared in the previous step.

## Usage

1. **Create a GitHub Token Secret:**
   You need to create a GitHub token with the necessary permissions to deploy to GitHub Pages. To keep this token secure, it's recommended to store it as a secret in your repository. The secret should be named `Workflow_Token`.

2. **Configure the Workflow:**
   To use this workflow, you can create a `.github/workflows/gh-pages.yml` file in your repository and paste the workflow code into it.


3. **Push Changes:** Whenever you push changes to the `main` branch, this workflow will automatically build and deploy your website to GitHub Pages.

4. **Access Your Deployed Site:**
   After the workflow completes successfully, you can access the deployed website on GitHub Pages at `https://<username>.github.io/<repository-name>`.

Make sure to adapt this workflow to your specific needs, such as modifying the build process or the directory structure as necessary.
