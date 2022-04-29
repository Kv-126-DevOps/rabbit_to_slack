# Rabbit-to-slack

This application grabs data from RabbitMQ queue and send to Slack

### Create Slack Webhook URL

In the article "Sending an automated message to slack using python" you can find how to connect "Incoming Webhooks to slack" create Webhook URL that will be as SLACK_URL variable  [link](https://medium.com/@sharan.aadarsh/sending-notification-to-slack-using-python-8b71d4f622f3)
### Run rabbit-to-bd
    git clone --branch 1-rabbit-to-slack-code-refactoring https://github.com/Kv-126-DevOps/rabbit_to_slack.git /opt/rabbit-to-slack
    docker run --network=kv126 RABBIT_HOST=rabbit -e RABBIT_PORT=5672 -e RABBIT_USER=mquser -e RABBIT_PW=mqpass -e RABBIT_QUEUE=slack -e SLACK_URL=<specify slack webhook urk>   -d --name rabbit-to-slack -v /opt/rabbit-to-slack:/app python:3.9-slim sleep infinity
    docker exec rabbit-to-slack  pip install -r /app/requirements.txt
    docker exec -d rabbit-to-slack bash -c "cd /app && python ./app.py"
	

