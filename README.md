# Sentiment Analysis Project: MuleSoft MCP + Salesforce + Gemini

This project demonstrates how to integrate **MuleSoft**, **Salesforce**, the **MCP (Model Context Protocol) connector**, and **Gemini AI** to perform sentiment analysis on customer comments and automatically update Salesforce Cases based on the results.

The solution simulates a modern, intelligent integration pipeline where customer feedback is analyzed using generative AI, and the results are recorded in Salesforce. This can be applied to enhance customer service, automate case triage, or extract insights from support interactions.

## Use Cases

- Automatically classify customer comments (e.g., from support tickets or surveys)
- Populate Salesforce Cases with sentiment insights
- Improve case prioritization or routing based on sentiment
- Introduce AI-driven automation into CRM processes

## Components

- **MCP Client API**: Exposes an HTTP endpoint that receives incoming requests containing a case number and comment and invokes the MCP Server using the official MCP connector to trigger the sentiment analysis process.
- **MCP Server API**: Uses Gemini to analyze the sentiment and updates the corresponding Case in Salesforce with the sentiment label and confidence score.

## Technologies Used

- Mule 4.9
- MuleSoft MCP Connector
- Google Gemini API
- Salesforce Developer Edition

## API Usage

**Base URL (local):** [`http://localhost:8081/analyze-sentiment`](http://localhost:8081/analyze-sentiment)  
**Method:** `POST`  
**Content-Type:** `application/json`

### Example Request

```json
{
    "caseNumber": "15001002",
    "comment": "I hated the product"
}
```

### Example Response

```json
{
    "sentiment": "negative",
    "score": "0.95"
}
```

## Configuration

Before running the APIs, make sure to configure the required properties. These values should be placed in your environment-specific property file (e.g., `dev.yaml`).

### Required Properties

| Property              | Description                             |
|-----------------------|-----------------------------------------|
| `gemini-api.key`      | API key for accessing the Gemini API  |
| `salesforce.user`     | Salesforce username (Developer Edition) |
| `salesforce.password` | Salesforce password                     |
| `salesforce.token`    | Salesforce security token               |

> **Important**: Do not hardcode these values in your flows. Use property placeholders (`${property.name}`) and secure property files.

### Runtime Argument

When running your Mule application locally, make sure to specify the environment using the following VM argument:

```bash
-M-Dmule.env=dev
```

## Authors

**Andrea Da Silva**: [LinkedIn](https://www.linkedin.com/in/andreavdasilvab) | [Medium](https://medium.com/@andreadasilvab).

Feel free to reach out for any questions or collaborations!