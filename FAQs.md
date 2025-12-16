# Frequently Asked Questions

### Why does it only cover up to 9 teams?
I built up to 9 teams as that was the max I could fit in the report page with the visuals chosen. You could copy the existing approaches if you wanted to add more teams and feel free to submit a PR if you find a way to add more!

### How many simulations does it run?
For performance reasons, it only does 500 simulations per team. As it runs per team and then overall this is ~9000 simulations in total. There may be slight differences from a model that uses 10,000 sims per team but only a few days. Here is a comparison:

<img width="1797" height="580" alt="image" src="https://github.com/user-attachments/assets/ddb48969-3ccf-42ff-b8f9-21342c9be984" />

### Why does it seem to be slow/sluggish?
Power BI isn't the best at performance of this type of thing. What I will say is it does cache when you have run forecasts so you can expect performance to speed up if you only make a few changes.

### How do I share this?
To share this you should publish the file to your respective Power BI workspace/web service.

### Can I try it out first?
There is a web-based version with anonymised data available [here](https://app.powerbi.com/view?r=eyJrIjoiNGM0MjE1ZTEtY2RjNi00MDc3LWIxODgtZDJlMDIxMDQ0Y2JjIiwidCI6IjVjYzc5MjVjLWY4MjQtNDJlZC1iYTY0LTRmYzUxMDlhYzE5YyJ9) where you can see it in action, along with some scenarios to experiment with

### Why do I have to add BLANK and 0 for the ADO version?
The ADO version uses the OData ADO data source and this doesn't allow dynamic data sources in the Power BI service, meaning users wouldn't be able to schedule a refresh if published. This is a workaround for that so that users can share it (as well as it being a Power BI templated app).

### How do I get this on a mac?
Mac users will have to use the templated app which is available for Jira [here]() and ADO [here]()
