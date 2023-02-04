
# A composite GitHub Action to login to the HuggingFace Hub

You can add this action to your workflow to easily login to the huggingface hub

- To hide your token from the logs and commit history, you can use the secrets feature of GitHub Actions.

Example workflow:

```
on: [push]

jobs:
  example-job:
    runs-on: ubuntu-latest
    steps:
      - name: Checkout
        uses: actions/checkout@v2

      - name: Login to HuggingFace Hub
        uses: osbm/huggingface_login@v0.1
        with:
          username: ${{ secrets.HF_USERNAME }}
          password: ${{ secrets.HF_PASSWORD }}
          add_to_git_credentials: true

      - name: Check if logged in
        run: |
          huggingface-cli whoami
```