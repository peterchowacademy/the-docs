---
title: Typescript-yarn
layout: default
parent: Frontend
grand_parent: Coding Practices
---

# Typescript ts
{: .no_toc }

## Table of contents
{: .no_toc .text-delta }

1. TOC
{:toc}

---
# Vite Project setup

## Build tools for generate application
- Vite 
To trigger Vite to create a project from scratch `npm create vite@latest`

- nextjs

- create react app
## Framework
- vanilla
- vue
- react
- preact
- lit
- svelte

## Variant
- javascript
- typescript


# Typescript project setup

## Base settings

1. Refresh your local package index `sudo apt update` and enter sudo password
2. Install node.js `sudo apt install nodejs` and press Y and enter
3. If yarn is not recognized as an internal or external command, try installing yarn globally `npm install -g yarn`
4. Try running `npm run start`

Option knowledge:
- Since we're using ubuntu wsl as our remote env, sudo install nodejs will install on windows instead of on Ubuntu

- Check `which npm` 
    - if the output is /mnt/c/ubuntu.... this is not what we want
    - We expect something like /usr/local/...

- Solution: Install npm directly on Ubuntu (please refer to [Windows setup](https://learn.microsoft.com/en-us/windows/dev-environment/javascript/nodejs-on-wsl))
    - `curl -o- https://raw.githubusercontent.com/nvm-sh/nvm/master/install.sh | bash`
    - `source ~/.bashrc`
    - Check if nvm is installed `nvm -v`
    - If yes, install latest LTS stable version of node.js `nvm install --lts`
    - Check what node js was installed on nvm `nvm ls`
    - At this point check `which node` if it's /home/usr/... then CONGRATS

## Final wrap up
- Install next globally `npm i -g next`
- Bring back your node_modules first : `npm install`
- Fix vulnerability on tailwind `npm audit fix`
- Clean up working area `npm run clean`
- Build project `npm run build`
- Host the project on localhost `npm run start`

# Coding commences

## Adding a youtube svg icon
1. You can download the 
2. To visualize the svg path d attribute inputs, visit [svg path visualizer](https://svg-path-visualizer.netlify.app/#) webpage
3. To modify the svg paths (inlcuding scaling, translating...), you can try this [svg path editor](https://yqnn.github.io/svg-path-editor/) 
4. Trying to commit directly on the main branch

# Deploying to github pages
1. Add `output:'export',` to your next.config.js under nextConfig
2. Make sure everything is at relative paths `../xyz.tsx`
3. Commit Changes, and head to settings page of your repo
4. Settings -> Pages, source pick github action
5. Click browse all workflows, and search next -> Configure
6. Commit changes, submit and that's it

For more details please refer to [this youtube video](https://www.youtube.com/watch?v=WoL3xbkAfOU)
{:.warning}