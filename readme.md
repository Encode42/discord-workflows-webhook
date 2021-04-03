# Discord Webhook for Github Actions
**Modified to have the same style as the default GitHub webhook.**  
This is mainly for my own personal use! There will be little to no support provided.

## Setup
1. In Github secrets, add a `WEBHOOK_URL` variable with the Discord web hook URL.
2. Inside your workflow file, add this snippet after the build-critical task:

    ```yaml
        - name: Send Webhook Notification
          if: always()
          run: |
            git clone https://github.com/Encode42/discord-workflows-webhook.git webhook
            bash webhook/send.sh ${{ job.status }} ${{ secrets.WEBHOOK_URL }}
          shell: bash
    ```

    <sub>To see a working example, look at [this workflow file](https://github.com/CraftLight-Network/Fish/blob/main/.github/workflows/run.yml).</sub>  
3. That's all! Webhook notifications will automatically be sent on every workflow run.
