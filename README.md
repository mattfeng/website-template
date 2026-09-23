# Personal website template

- This website is based off of the [portfolio-blog-starter](https://portfolio-blog-starter.vercel.app) Vercel template: https://github.com/vercel/examples/tree/main/solutions/blog

## Instructions

### 0. Set up your development environment

- If you're using Windows, do everything from a Linux distro (e.g. Ubuntu) running on WSL. All the instructions below assume a Linux/UNIX based development environment.
- If you're using macOS, you will need to install [Homebrew](https://brew.sh/).
    - Be sure to run the post-install commands displayed by the installation script displays after it completes.
    - You will need to open a new terminal window after running the post-install commands.
- Install Fast Node Manager (`fnm`).
    - WSL users will need to first install `unzip` by running the following commands:
       ```bash
       sudo apt update
       sudo apt install unzip
       ```
    - Then install `fnm` by following the instructions [in the repo](https://github.com/schniz/fnm).
    - You will need to open a new terminal window again after you install `fnm` in order for terminal to update its `PATH` variable and properly load/configure `fnm`.
    - Once `fnm` is installed, install the latest stable versions of NodeJS using the following commands:
        ```bash
        fnm install --lts --use
        fnm default $(fnm current)
        ```

### 1. Fork, then clone, this repo

- **For all instructions, replace `YOUR_GITHUB_USERNAME` with your actual GitHub username.**
- Fork this repository into your own GitHub account. Name the forked repository `YOUR_GITHUB_USERNAME.github.io`.
    - The repository can be private if you have GitHub Pro, which you can get for free by signing up for the [GitHub Student Developer Pack](https://education.github.com/pack/join). You can always make the repository private at a later date as well.
- Once you've forked the repository into your personal GitHub account, clone it with the following commands:
    ```bash
    cd ~
    git clone git@github.com:YOUR_GITHUB_USERNAME/YOUR_GITHUB_USERNAME.github.io
    ```

### 2. Configure your website

- Open the folder of the repository you just cloned onto your computer (i.e. `YOUR_GITHUB_USERNAME.github.io`) in VSCode.
- In the terminal, start the **live development server** so you can get a preview of what the changes you make look like on the website. Run the following commands:
    ```bash
    cd ~/YOUR_GITHUB_USERNAME.github.io
    npm install
    npm run dev
    ```
    - Open the link that is output to the terminal in your browser (it should be `http://localhost:3000`, although the port number 3000 may be different). You should see the live development server rendering your website.
- Edit `app/config.js` with your personal information.
- You can also choose custom fonts to use on the website. [Google Fonts](https://fonts.google.com/) is a reliable source of free fonts to choose from.
- Edit `app/projects/data.ts` with past projects you'd like to showcase.
    - Put photos in `public/projects/` (create the folder if needed) and use filenames relative to `public/`, such as `"example-project/my-project.jpg"`.

### 3. Set up GitHub Actions

- After creating or forking your project, run:
    ```bash
    cd ~/YOUR_GITHUB_USERNAME.github.io
    bash setup-github.sh
    ```
- This creates `.github/workflows/deploy.yml` from the template embedded in the script, so the workflow can be added in a new commit in your own repository.
- The workflow builds the site with Node.js 24 and deploys `out/` to GitHub Pages.

### 4. Commit your changes and push to GitHub

- Once you've made edits to your website, you can save (commit) those changes and then push them to GitHub. First, we will make sure our `git` is fully configured:
   ```bash
    git config --global user.email "REPLACE WITH YOUR GITHUB ACCOUNT EMAIL"
    git config --global user.name "REPLACE WITH YOUR NAME"
   ```
- Make sure you're in the top-level folder of the repo, i.e. `YOUR_GITHUB_USERNAME.github.io`, and run the following commands:
    ```bash
    git add .
    git status
    git commit -m 'add personal info'
    git status
    git push
    ```
- Assuming everything goes well, your website should now be uploaded to GitHub.

### 5. Enable GitHub Pages

- Finally, ensure [GitHub Actions is enabled](https://docs.github.com/en/repositories/managing-your-repositorys-settings-and-features/enabling-features-for-your-repository/managing-github-actions-settings-for-a-repository) in the new repository. On the GitHub site for your repository (`https://github.com/YOUR_GITHUB_USERNAME/YOUR_GITHUB_USERNAME.github.io`), go to **Settings > Pages > Build and deployment**, select **GitHub Actions** as the [publishing source](https://docs.github.com/en/pages/getting-started-with-github-pages/configuring-a-publishing-source-for-your-github-pages-site).
- Wait for the GitHub Action to run, and if successful, you should see your website active at https://YOUR_GITHUB_USERNAME.github.io/.

### 6. Updating your website

- Now, if you want to continue updating your website, you can do so by editing the files in the repository, i.e. the `YOUR_GITHUB_USERNAME.github.io` folder.
- Then, once you are satisfied with the changes, run the following commands (`#` means comment, and so you don't need to copy/type those lines):
    ```bash
    # make sure you're in the top-most level of the repository folder
    cd ~/YOUR_GITHUB_USERNAME.github.io
    # tell git you want to save all the edits made ("staging")
    git add .
    # permanently record the changes ("commit the changes")
    git commit -m "REPLACE THIS WITH A RELEVANT SUMMARY OF CHANGES MADE"
    # upload the changes to GitHub, which will also rebuild and deploy your website
    git push
    ```
- Once your [GitHub Student Developer Pack application](https://education.github.com/pack/join) is approved,

## Reference portfolios

Here are some portfolio websites to use as inspiration:

- https://avaamini.com/
- https://paco.me/
- https://andymatuschak.org/
- https://foliobin.com/
- [https://www.are.na/kelindi/personal-sites-_sxervw2jmu](https://www.are.na/kelindi/personal-sites-_sxervw2jmu)
- https://macwright.com/
- https://www.mikes.cv/
- https://www.arlan.me/

## Development notes

- Use Node.js 20.9 or later (Node.js 24 is used in CI and the dev container). The app targets Next.js 16.3.5 with React 19.
- The site uses `output: "export"` for GitHub Pages and deploys the generated `out/` directory.
