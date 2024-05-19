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
2. To visualize the svg path d attribute inputs, visit [this](https://svg-path-visualizer.netlify.app/#) webpage
3. To modify the svg paths (inlcuding scaling, translating...), you can try this [svg path editor](https://yqnn.github.io/svg-path-editor/) 