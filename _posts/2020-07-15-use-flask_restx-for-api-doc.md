---
title: Use flask-restx for API Documentation
author: Yan Zhang
date: 2020-07-15 20:55:00 +0800
categories: [Tutorial]
tags: [Python, Flask]
pin: true
---

## Why use flask-restx

Flask-RESTX is an extension for Flask that adds support for quickly building REST APIs. And this package could help  us to render swagger ui from server side. [Offical Docs](https://flask-restx.readthedocs.io/en/latest/)



## Install

```shell
pip install flask-restx
```



## Quick Start 

```python
from flask_restx import Resource, Api, fields, Namespace
from flask import Flask, Blueprint

app = Flask(__name__)

api = Api(
    title="My Flask APP", version="1.0", doc="/doc/", ordered=True
)

ns = Namespace("Sample", description="sample namesapce")

resource_fields = ns.model('Resource', {
    'name': fields.String,
    'network': fields.Float
})

api.add_namespace(ns, path="/api")

@hello.route('/')
class HelloWorld(Resource):
    @api.doc(body=resource_fields)
    @api.response(200, "Success", api.models["resource_fields"])
    def get(self):
        return {'hello': 'world'}
    def post(self):
        return {'a': 'b'}
    def patch(self):
        return {'c': 'c'}
    def delete(self):
        return {'d': 'd'}
      
      
if __name__ == "__main__":
    app.run(debug=False, host="0.0.0.0", port=8000)
```

After we run flask app, api docs will be shown on `/doc` endpoint
