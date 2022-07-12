---
layout: post
title: "How to deploy a Flask powered Python REST API on Vercel for free?"
date: 2022-07-12 12:00:00 +0530
categories: python
tags: python flask vercel cors
---
We all love free tools and platforms to get started on coding or to prototype.

Did you know that you can deploy a Flask powered Python REST API on Vercel for free? Here's how to do it.

Begin by creating a folder to contain your code.

We'll name our main Python script as "index.py".

```python
from flask import Flask, jsonify
from flask_cors import CORS


app = Flask(__name__)
CORS(app)

@app.route('/')
def home():
    return jsonify({"data":"Your important data"})
```

Here we use Flask and flask_cors (to enable CORS).

Now create a JSON file named "vercel.json" in the same folder. This file includes the configuration for Vercel to build our app.

```json
{
    "version": 2,
    "builds": [
        {
            "src": "./index.py",
            "use": "@vercel/python"
        }
    ],
    "routes": [
        {
            "src": "/(.*)",
            "dest": "/"
        }
    ]
}
```

Finally create a "requirements.txt" file on the same directory and enter the following dependencies in it.

```txt
Flask
flask_cors
```

Now we are ready to deploy. You can either use the Vercel CLI or Github for deploying. For this example we will use vercel-cli. Configure it using the instructions given [here](https://vercel.com/docs/concepts/deployments/overview#vercel-cli).

Just type "vercel" (or "vercel --prod" for production release) on a terminal inside the same directory. In a few seconds your project will be live and you can actually preview the building process and output on the Vercel [dashboard](https://vercel.com/dashboard).

However, there are some [limitations](https://vercel.com/docs/concepts/limits/overview) for the invocations of functions using the Hobby plan.

Hope you will find this useful at some point. 

### Happy coding!