## Custom Traffic Alexa Skill

A scheduled task would run every morning to pull the traffic data and store results in the `exportable_json` variable.  An endpoint was
created as a flask view that would return var along with mimetype *application/json*, this was a requirement for alexa to process the content

```python
@app.route('/alexa_flash')
@login_required
def alexa_flash():
    json_data = exportable_json
    return Response(response=json_data, mimetype='application/json')
```

check the alexa request/response [docs](https://developer.amazon.com/docs/custom-skills/request-and-response-json-reference.html) to confirm if new response format is needed. The `main.py` file works as expected 
