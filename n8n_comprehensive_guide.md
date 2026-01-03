# n8n Workflow Automation: A Comprehensive Guide from Beginner to Advanced

## Introduction

n8n is a free, open-source workflow automation platform that allows you to connect different services, APIs, and databases to create powerful automation workflows. Unlike many cloud-only automation tools, n8n can be self-hosted, giving you complete control over your data and infrastructure.

This guide will take you from zero knowledge to building production-ready automation workflows. You will learn the core concepts, installation methods, practical workflow development, and advanced techniques for building robust automations.

## What is n8n?

n8n (pronounced "n-eight-n") is a node-based workflow automation tool. It provides a visual interface where you design workflows by connecting nodes that represent different actions, services, or transformations. Data flows from one node to the next, enabling you to build complex automation logic without writing extensive code.

### Key Features

- Visual workflow builder with drag-and-drop interface
- 400+ integrations with popular services and APIs
- Self-hosting capability for complete data control
- Fair-code license (sustainable open-source model)
- Built-in support for custom JavaScript and Python code
- Real-time and scheduled workflow execution
- Webhook support for event-driven automation
- Error handling and retry mechanisms
- Version control and workflow templates

## Understanding n8n Architecture

### Core Components

**Workflows**: A workflow is a collection of connected nodes that execute in sequence or parallel to automate a process. Each workflow has a unique ID and can be activated or deactivated.

**Nodes**: Nodes are the building blocks of workflows. Each node performs a specific action such as fetching data from an API, transforming data, sending an email, or making a decision based on conditions.

**Triggers**: Triggers are special nodes that start workflow execution. They can be time-based (cron schedules), event-based (webhooks), or manual.

**Credentials**: Credentials store authentication information for external services. They are encrypted and reusable across multiple workflows.

**Executions**: Each time a workflow runs, it creates an execution record that logs all data passing through nodes, errors, and execution time.

**Items**: Data in n8n is organized as items. Each item is a JSON object. Nodes can process multiple items in a single execution, and each item flows through the workflow independently.

### Execution Model

n8n uses an event-driven execution model:

1. A trigger activates the workflow
2. The workflow engine processes nodes sequentially based on connections
3. Data is passed from one node to the next as JSON
4. If a node fails, error handling logic determines the next step
5. Execution completes when all connected nodes have been processed

The workflow engine can run in different modes:

- **Main Process**: Single-process execution suitable for small deployments
- **Queue Mode**: Uses a job queue (Bull with Redis) to distribute execution across multiple worker processes for scalability

### Data Flow

Data in n8n flows between nodes in a standardized format. Each node receives an array of items and outputs an array of items. An item has this structure:

```json
{
  "json": {
    "field1": "value1",
    "field2": "value2"
  },
  "binary": {
    "data": {
      "data": "base64EncodedData",
      "mimeType": "image/png",
      "fileName": "example.png"
    }
  }
}
```

The `json` property contains structured data, while the `binary` property holds file data.

## Installation and Setup

### Option 1: Cloud Installation

The fastest way to start with n8n is using the cloud version.

1. Visit https://n8n.io
2. Click "Get started for free"
3. Create an account using email or OAuth
4. You will be directed to your n8n instance dashboard
5. Start building workflows immediately

Cloud benefits:
- No installation required
- Automatic updates
- Managed infrastructure
- Built-in SSL/TLS

Cloud limitations:
- Execution time limits on free tier
- Cannot use custom nodes without upgrading
- Data stored on n8n servers

### Option 2: Installation via npm

Requirements:
- Node.js 18.x or later
- npm 9.x or later

**Step 1: Install Node.js**

Download and install Node.js from https://nodejs.org. Verify installation:

```bash
node --version
npm --version
```

**Step 2: Install n8n globally**

```bash
npm install n8n -g
```

**Step 3: Start n8n**

```bash
n8n
```

n8n will start and be accessible at http://localhost:5678

**Step 4: Configure environment variables (optional)**

Create a `.env` file or set environment variables:

```bash
export N8N_BASIC_AUTH_ACTIVE=true
export N8N_BASIC_AUTH_USER=admin
export N8N_BASIC_AUTH_PASSWORD=yourpassword
export N8N_HOST=0.0.0.0
export N8N_PORT=5678
export N8N_PROTOCOL=http
export WEBHOOK_URL=http://localhost:5678/
```

Restart n8n with:

```bash
n8n start
```

**Step 5: Running n8n persistently with PM2**

Install PM2 process manager:

```bash
npm install pm2 -g
```

Start n8n with PM2:

```bash
pm2 start n8n
pm2 save
pm2 startup
```

This ensures n8n starts automatically after system reboot.

### Option 3: Installation via Docker

Requirements:
- Docker 20.x or later
- Docker Compose (optional but recommended)

**Step 1: Create a directory for n8n**

```bash
mkdir ~/n8n-docker
cd ~/n8n-docker
```

**Step 2: Create docker-compose.yml**

```yaml
version: '3.8'

services:
  postgres:
    image: postgres:15
    restart: always
    environment:
      POSTGRES_USER: n8n
      POSTGRES_PASSWORD: n8n_password
      POSTGRES_DB: n8n
    volumes:
      - postgres_data:/var/lib/postgresql/data
    healthcheck:
      test: ['CMD-SHELL', 'pg_isready -h localhost -U n8n']
      interval: 5s
      timeout: 5s
      retries: 10

  n8n:
    image: n8nio/n8n:latest
    restart: always
    ports:
      - '5678:5678'
    environment:
      DB_TYPE: postgresdb
      DB_POSTGRESDB_HOST: postgres
      DB_POSTGRESDB_PORT: 5432
      DB_POSTGRESDB_DATABASE: n8n
      DB_POSTGRESDB_USER: n8n
      DB_POSTGRESDB_PASSWORD: n8n_password
      N8N_BASIC_AUTH_ACTIVE: 'true'
      N8N_BASIC_AUTH_USER: admin
      N8N_BASIC_AUTH_PASSWORD: changeme
      WEBHOOK_URL: http://localhost:5678/
      GENERIC_TIMEZONE: Europe/Berlin
    volumes:
      - n8n_data:/home/node/.n8n
    depends_on:
      postgres:
        condition: service_healthy

volumes:
  postgres_data:
  n8n_data:
```

**Step 3: Start n8n**

```bash
docker-compose up -d
```

**Step 4: Access n8n**

Open http://localhost:5678 in your browser.

**Step 5: View logs**

```bash
docker-compose logs -f n8n
```

**Step 6: Stop n8n**

```bash
docker-compose down
```

To remove all data:

```bash
docker-compose down -v
```

### Option 4: Installation with Docker (Simplified)

For quick testing without a database:

```bash
docker run -it --rm   --name n8n   -p 5678:5678   -v ~/.n8n:/home/node/.n8n   n8nio/n8n
```

This runs n8n with SQLite storage in your home directory.

### Initial Configuration

When you first access n8n, you will be prompted to:

1. Create an owner account (email and password)
2. Optionally connect to n8n cloud for templates and community workflows
3. Set up your first workflow

## Beginner: Building Your First Workflows

### The n8n Interface

When you open n8n, you will see:

- **Workflows panel** (left): List of all your workflows
- **Canvas** (center): Visual workflow editor where you connect nodes
- **Node panel** (right): Available nodes you can add
- **Execution panel** (bottom): Shows execution history and data

### Understanding Nodes

Nodes are categorized as:

- **Trigger Nodes**: Start workflows (webhook, cron, manual trigger)
- **Action Nodes**: Perform operations (HTTP Request, database queries, send email)
- **Function Nodes**: Transform data (Function, Code, Set, IF, Switch, Merge)

### Creating Your First Workflow

**Example 1: Manual Trigger with HTTP Request**

Goal: Fetch data from a public API and display it.

1. Click "Add Workflow" to create a new workflow
2. Click the "+" button on the canvas
3. Search for "Manual Trigger" and select it
4. Click the "+" to the right of the Manual Trigger node
5. Search for "HTTP Request" and select it
6. Configure the HTTP Request node:
   - Method: GET
   - URL: https://api.coindesk.com/v1/bpi/currentprice/BTC.json
7. Click "Execute Node" to test
8. You will see Bitcoin price data in the output panel

**Understanding Output Data**

The HTTP Request node outputs data in this format:

```json
{
  "json": {
    "time": {...},
    "disclaimer": "...",
    "bpi": {
      "USD": {
        "code": "USD",
        "rate": "45000.00",
        "description": "United States Dollar"
      }
    }
  }
}
```

### Working with Expressions

Expressions allow you to reference data from previous nodes dynamically.

**Example 2: Extract Specific Data**

Continuing from Example 1:

1. Add a "Set" node after HTTP Request
2. In the Set node, add a field:
   - Name: bitcoin_price
   - Value: Click "Expression" toggle, then enter:
     ```
     {{ $json.bpi.USD.rate }}
     ```
3. Execute the node
4. The output will contain only the bitcoin price

Expression syntax:
- `{{ }}` wraps expressions
- `$json` references the JSON data from the previous node
- Dot notation accesses nested properties
- `$json['property']` alternative bracket notation

### Common Expression Variables

- `$json`: JSON data from previous node
- `$binary`: Binary data from previous node
- `$input.all()`: Data from all items in previous node
- `$input.first()`: First item from previous node
- `$input.last()`: Last item from previous node
- `$node["NodeName"].json`: Data from a specific node
- `$now`: Current timestamp
- `$today`: Current date
- `$workflow`: Workflow metadata
- `$execution`: Execution metadata

### Mini-Project 1: Fetch Weather Data and Send Telegram Alert

**Goal**: Get current weather for a city and send an alert to Telegram.

**Prerequisites**: Create a Telegram bot and get the bot token and chat ID.

**Steps**:

1. **Add Manual Trigger**
   - This will start the workflow on demand

2. **Add HTTP Request Node** (Get Weather)
   - Method: GET
   - URL: `https://api.open-meteo.com/v1/forecast?latitude=52.52&longitude=13.41&current_weather=true`
   - This fetches weather for Berlin (change coordinates for your city)

3. **Add Set Node** (Format Message)
   - Click "Add Field" > String
   - Name: message
   - Value (Expression):
     ```
     Weather Update: Temperature is {{ $json.current_weather.temperature }}°C, Wind speed: {{ $json.current_weather.windspeed }} km/h
     ```

4. **Add Telegram Node**
   - First, create Telegram credentials:
     - Click "Select Credentials" > "Create New"
     - Name: My Telegram Bot
     - Access Token: Your bot token from BotFather
     - Save
   - Configure node:
     - Chat ID: Your chat ID
     - Text: Use expression `{{ $json.message }}`

5. **Execute Workflow**
   - Click "Execute Workflow" button
   - Check your Telegram for the weather message

6. **Activate Workflow**
   - Toggle "Active" switch at top right
   - Change the Manual Trigger to a Schedule Trigger if you want periodic updates

**Schedule Trigger Configuration**:
- Remove Manual Trigger
- Add "Schedule Trigger" node
- Set Trigger Interval: Every 6 hours
- Mode: Every X
- Value: 6
- Unit: Hours

Now the workflow runs automatically every 6 hours.

### Working with Webhook Triggers

Webhooks allow external services to trigger your workflows.

**Example 3: Webhook to Log Data**

1. Add "Webhook" trigger node
2. HTTP Method: POST
3. Path: data-receiver
4. Copy the "Test URL" (appears after saving)
5. Add "Set" node to extract webhook data
6. Add "HTTP Request" node to send data to a logging service or database

**Testing the Webhook**:

Use curl or Postman:

```bash
curl -X POST https://your-n8n-instance/webhook-test/data-receiver   -H "Content-Type: application/json"   -d '{"name": "John", "email": "john@example.com"}'
```

Access data in subsequent nodes using:
```
{{ $json.body.name }}
{{ $json.body.email }}
```

### Node Configuration Best Practices

- **Always test nodes individually**: Use "Execute Node" before running entire workflow
- **Pin data**: Click the pin icon on a node's output to use that data for testing downstream nodes
- **Use descriptive node names**: Rename nodes by clicking the node name
- **Add notes**: Right-click canvas > Add Note to document complex logic

### Understanding Items and Batching

n8n processes data in items. If a node outputs 3 items, the next node processes all 3.

**Example 4: Processing Multiple Items**

1. **Add Manual Trigger**
2. **Add Function Node** (Generate Items)
   - Code:
     ```javascript
     return [
       { json: { city: "Berlin", country: "Germany" } },
       { json: { city: "Paris", country: "France" } },
       { json: { city: "London", country: "UK" } }
     ];
     ```
3. **Add HTTP Request Node** (Get Weather for Each City)
   - URL expression:
     ```
     https://api.open-meteo.com/v1/forecast?latitude=52.52&longitude=13.41&current_weather=true
     ```
   - Note: You would need actual coordinates per city in production

The HTTP Request node executes once per item, making 3 API calls.

### Conditional Logic with IF Node

**Example 5: Route Data Based on Condition**

1. **Add Manual Trigger**
2. **Add Function Node** (Generate Random Number)
   ```javascript
   return [{ json: { number: Math.floor(Math.random() * 100) } }];
   ```
3. **Add IF Node**
   - Condition: Number
   - Value 1: `{{ $json.number }}`
   - Operation: Larger
   - Value 2: 50
4. **Add Set Node to "true" output**
   - Name: High Number
5. **Add Set Node to "false" output**
   - Name: Low Number

Execute workflow multiple times to see different paths activate.

### Error Handling Basics

**Enable Continue On Fail**:
1. Click a node
2. Go to Settings tab
3. Enable "Continue On Fail"
4. If this node errors, workflow continues instead of stopping

**Example 6: Handle HTTP Request Errors**

1. **Add HTTP Request Node**
   - URL: https://jsonplaceholder.typicode.com/posts/1
   - Settings > Continue On Fail: Enabled
2. **Add IF Node** (Check for Error)
   - Condition: Boolean
   - Value 1: `{{ $json.error !== undefined }}`
   - Operation: Equal
   - Value 2: true
3. **Add nodes to handle error path**

### Mini-Project 2: Form Submission Handler

**Goal**: Receive form data via webhook, validate it, store in Google Sheets.

**Prerequisites**: Set up Google Sheets API credentials in n8n.

**Steps**:

1. **Add Webhook Trigger**
   - HTTP Method: POST
   - Path: form-submit

2. **Add Set Node** (Extract Form Data)
   - Add fields:
     - name: `{{ $json.body.name }}`
     - email: `{{ $json.body.email }}`
     - message: `{{ $json.body.message }}`

3. **Add IF Node** (Validate Email)
   - Condition: String
   - Value 1: `{{ $json.email }}`
   - Operation: Contains
   - Value 2: @

4. **True Path: Add Google Sheets Node**
   - Operation: Append
   - Document: Select your spreadsheet
   - Sheet: Sheet1
   - Columns:
     - name: `{{ $json.name }}`
     - email: `{{ $json.email }}`
     - message: `{{ $json.message }}`
     - timestamp: `{{ $now.toISO() }}`

5. **True Path: Add Webhook Response Node**
   - Response Code: 200
   - Response Body: `{"status": "success", "message": "Form submitted"}`

6. **False Path: Add Webhook Response Node**
   - Response Code: 400
   - Response Body: `{"status": "error", "message": "Invalid email"}`

7. **Activate Workflow**

**Test with HTML Form**:

```html
<!DOCTYPE html>
<html>
<body>
  <form id="contactForm">
    <input type="text" name="name" placeholder="Name" required>
    <input type="email" name="email" placeholder="Email" required>
    <textarea name="message" placeholder="Message" required></textarea>
    <button type="submit">Submit</button>
  </form>

  <script>
    document.getElementById('contactForm').addEventListener('submit', async (e) => {
      e.preventDefault();
      const formData = {
        name: e.target.name.value,
        email: e.target.email.value,
        message: e.target.message.value
      };

      const response = await fetch('YOUR_WEBHOOK_URL', {
        method: 'POST',
        headers: { 'Content-Type': 'application/json' },
        body: JSON.stringify(formData)
      });

      const result = await response.json();
      alert(result.message);
    });
  </script>
</body>
</html>
```

## Intermediate: Advanced Workflow Techniques

### Data Transformation with Function Node

The Function node allows custom JavaScript for complex transformations.

**Example 7: Transform Array Data**

Input data (from previous node):
```json
{
  "users": [
    {"name": "Alice", "age": 30},
    {"name": "Bob", "age": 25}
  ]
}
```

Function node code:
```javascript
const users = $input.first().json.users;

return users.map(user => ({
  json: {
    fullName: user.name.toUpperCase(),
    ageInMonths: user.age * 12,
    category: user.age >= 30 ? 'senior' : 'junior'
  }
}));
```

Output:
```json
[
  {"fullName": "ALICE", "ageInMonths": 360, "category": "senior"},
  {"fullName": "BOB", "ageInMonths": 300, "category": "junior"}
]
```

### Code Node: Python and JavaScript

The Code node provides more power than Function node and supports Python.

**Example 8: Python Data Processing**

```python
import json
from datetime import datetime

# Access items from previous node
items = _input.all()

output = []
for item in items:
    data = item['json']
    output.append({
        'json': {
            'processed_at': datetime.now().isoformat(),
            'uppercase_name': data.get('name', '').upper(),
            'name_length': len(data.get('name', ''))
        }
    })

return output
```

**Code Node vs Function Node**:
- Function node: Simpler, JavaScript only, faster for small tasks
- Code node: Both JavaScript and Python, better for complex logic, can use external libraries

### JSONata for Advanced Querying

JSONata is a query language for JSON data built into n8n.

**Example 9: Complex JSON Transformation**

Input:
```json
{
  "orders": [
    {"id": 1, "total": 100, "status": "paid"},
    {"id": 2, "total": 200, "status": "pending"},
    {"id": 3, "total": 150, "status": "paid"}
  ]
}
```

JSONata expression:
```
{{ $jmespath($json, "orders[?status=='paid'].total | sum(@)") }}
```

This filters orders with status "paid" and sums their totals, resulting in 250.

**Common JSONata Patterns**:

Filter array:
```
{{ $jmespath($json, "items[?price > `100`]") }}
```

Map array:
```
{{ $jmespath($json, "users[*].{name: name, id: id}") }}
```

Get first/last element:
```
{{ $jmespath($json, "items[0]") }}
{{ $jmespath($json, "items[-1]") }}
```

### Working with APIs: Authentication Methods

**API Key Authentication**:

HTTP Request node:
- Authentication: Generic Credential Type
- Select "Header Auth" credential
- Header Name: X-API-Key
- Header Value: your-api-key

**OAuth2 Authentication**:

Many nodes have built-in OAuth2 support. Example with Google Sheets:
1. Create credentials in Google Cloud Console
2. In n8n, create new Google Sheets credential
3. Enter Client ID and Client Secret
4. Click "Connect my account"
5. Authorize n8n

**Bearer Token**:

HTTP Request node:
- Authentication: Generic Credential Type
- Credential Type: Header Auth
- Name: Authorization
- Value: Bearer YOUR_TOKEN

**Basic Auth**:

HTTP Request node:
- Authentication: Generic Credential Type
- Select "Basic Auth"
- User: username
- Password: password

### Error Handling and Retries

**Configure Retry on Failure**:

1. Select a node prone to failures (API calls, database queries)
2. Settings tab
3. Retry On Fail: Enabled
4. Max Tries: 3
5. Wait Between Tries: 1000 (milliseconds)

**Error Workflow**:

Create a dedicated error-handling workflow:

1. Create new workflow "Error Handler"
2. Add "Error Trigger" node
3. Add nodes to:
   - Log error to database
   - Send notification to Slack/email
   - Create ticket in issue tracker

In your main workflow:
- Workflow Settings > Error Workflow > Select "Error Handler"

Now any error in main workflow triggers the error handler.

### Loop Node for Iteration

**Example 10: Process Items in Batches**

Use case: Process 100 items but API accepts only 10 at a time.

1. **Add Function Node** (Generate 100 items)
   ```javascript
   const items = [];
   for (let i = 1; i <= 100; i++) {
     items.push({ json: { id: i, value: `Item ${i}` } });
   }
   return items;
   ```

2. **Add Split In Batches Node**
   - Batch Size: 10

3. **Add HTTP Request Node** (Process Batch)
   - Send batch to API

4. **Loop back** to Split In Batches node until all processed

The Split In Batches node automatically handles iteration.

### Merge Node for Combining Data

**Example 11: Merge Data from Two Sources**

Scenario: Fetch user data from database and enrich with API data.

1. **Add Manual Trigger**

2. **Add PostgreSQL Node** (Fetch Users)
   - Operation: Execute Query
   - Query: `SELECT id, email FROM users LIMIT 10`

3. **Add HTTP Request Node** (Get Additional Data)
   - URL: `https://api.example.com/user-details/{{ $json.id }}`
   - This executes for each user

4. **Add Merge Node**
   - Mode: Combine
   - Combine By: Index
   - This merges database output with API output by position

Output will contain both database fields and API fields for each user.

### Mini-Project 3: Sync Google Sheets with REST API

**Goal**: Monitor a Google Sheet for new rows and POST them to a REST API.

**Steps**:

1. **Add Schedule Trigger**
   - Every 15 minutes

2. **Add Google Sheets Node** (Read Sheet)
   - Operation: Get Many
   - Document: Your spreadsheet
   - Sheet: Sheet1
   - Range: A2:D1000

3. **Add Function Node** (Track Processed Rows)
   ```javascript
   const newRows = [];
   const processedIds = $getWorkflowStaticData('node');

   if (!processedIds.lastRowId) {
     processedIds.lastRowId = 0;
   }

   const allRows = $input.all();

   for (const item of allRows) {
     const rowId = item.json.id;
     if (rowId > processedIds.lastRowId) {
       newRows.push(item);
       processedIds.lastRowId = rowId;
     }
   }

   return newRows;
   ```

4. **Add IF Node** (Check if New Rows Exist)
   - Condition: Number
   - Value 1: `{{ $json.length }}`
   - Operation: Larger
   - Value 2: 0

5. **True Path: Add HTTP Request Node** (POST to API)
   - Method: POST
   - URL: https://api.example.com/data
   - Body:
     ```json
     {
       "name": "={{ $json.name }}",
       "email": "={{ $json.email }}",
       "status": "={{ $json.status }}"
     }
     ```

6. **Activate Workflow**

This workflow polls Google Sheets every 15 minutes and sends only new rows to the API, tracking progress with static data.

### Working with Static Data

Static data persists between workflow executions.

**Access Static Data**:

In Function node:
```javascript
const staticData = $getWorkflowStaticData('node');

// Set value
staticData.lastProcessedId = 123;

// Get value
const lastId = staticData.lastProcessedId || 0;
```

Use cases:
- Track last processed item ID
- Store API rate limit reset time
- Maintain pagination cursors

### Environment Variables and Credentials

**Using Environment Variables**:

Set in your environment:
```bash
export MY_API_KEY=abc123
```

Reference in workflow expressions:
```
{{ $env.MY_API_KEY }}
```

**Credential Management Best Practices**:
- Never hardcode secrets in workflows
- Use n8n credentials system for API keys
- Set up separate credentials for dev/staging/production
- Regularly rotate credentials
- Use OAuth2 when available instead of API keys

### Working with Databases

**PostgreSQL Example**:

1. **Create Credential**
   - Credentials > Add Credential > Postgres
   - Host: localhost
   - Database: mydb
   - User: postgres
   - Password: yourpassword
   - Port: 5432

2. **Add PostgreSQL Node**
   - Operation: Execute Query
   - Query:
     ```sql
     INSERT INTO contacts (name, email, created_at)
     VALUES ('{{ $json.name }}', '{{ $json.email }}', NOW())
     RETURNING id
     ```

3. **Handle Query Results**
   - Query results are available as `$json` in next node

**MySQL, MongoDB, Redis**:

Similar setup process:
1. Create credentials
2. Add respective node
3. Configure operation (query, insert, update, delete)

### Mini-Project 4: Database-Driven Email Campaign

**Goal**: Query database for users who signed up in last 24 hours, send welcome email.

**Steps**:

1. **Add Schedule Trigger**
   - Every day at 9:00 AM

2. **Add PostgreSQL Node** (Fetch New Users)
   - Operation: Execute Query
   - Query:
     ```sql
     SELECT id, email, name
     FROM users
     WHERE created_at >= NOW() - INTERVAL '24 hours'
     AND welcome_email_sent = false
     ```

3. **Add IF Node** (Check Users Exist)
   - Condition: Boolean
   - Value 1: `{{ $json.length > 0 }}`
   - Operation: Equal
   - Value 2: true

4. **True Path: Add Gmail Node** (Send Email)
   - Operation: Send
   - To: `{{ $json.email }}`
   - Subject: Welcome to Our Platform
   - Email Type: Text
   - Message:
     ```
     Hi {{ $json.name }},

     Welcome to our platform! We're excited to have you on board.

     Best regards,
     The Team
     ```

5. **Add PostgreSQL Node** (Mark as Sent)
   - Operation: Execute Query
   - Query:
     ```sql
     UPDATE users
     SET welcome_email_sent = true
     WHERE id = {{ $json.id }}
     ```

6. **Activate Workflow**

This workflow runs daily, finds new users, sends welcome emails, and marks them as processed.

## Advanced: Production-Ready Workflows

### Building Reusable Subworkflows

Subworkflows allow you to modularize common logic.

**Create a Subworkflow**:

1. Create new workflow "Send Notification"
2. Add "Execute Workflow Trigger" node
3. Add logic to send notification via multiple channels (email, Slack, SMS)
4. Save workflow

**Use Subworkflow**:

In main workflow:
1. Add "Execute Workflow" node
2. Select "Send Notification" workflow
3. Pass data:
   ```json
   {
     "message": "{{ $json.alertMessage }}",
     "priority": "high"
   }
   ```

Benefits:
- Reusable across multiple workflows
- Centralized updates
- Cleaner main workflows

### Code Node Advanced Patterns

**Pattern 1: Async API Calls**

```javascript
const axios = require('axios');

const results = [];

for (const item of $input.all()) {
  const response = await axios.get(`https://api.example.com/data/${item.json.id}`);
  results.push({
    json: {
      ...item.json,
      apiData: response.data
    }
  });
}

return results;
```

**Pattern 2: Error Handling in Code**

```javascript
const results = [];

for (const item of $input.all()) {
  try {
    const data = JSON.parse(item.json.rawData);
    results.push({
      json: {
        ...data,
        parsed: true
      }
    });
  } catch (error) {
    results.push({
      json: {
        error: error.message,
        originalData: item.json.rawData,
        parsed: false
      }
    });
  }
}

return results;
```

**Pattern 3: Working with Binary Data**

```javascript
const items = $input.all();

return items.map(item => {
  const binaryData = item.binary.data;
  const buffer = Buffer.from(binaryData.data, 'base64');

  // Process buffer
  const processed = buffer.toString('utf-8').toUpperCase();

  return {
    json: {
      fileName: binaryData.fileName,
      processedContent: processed
    }
  };
});
```

### Custom Node Development

For repetitive tasks not covered by existing nodes, create custom nodes.

**Development Setup**:

1. Install n8n globally: `npm install n8n -g`
2. Create node project:
   ```bash
   mkdir n8n-nodes-mynode
   cd n8n-nodes-mynode
   npm init
   ```

3. Install dependencies:
   ```bash
   npm install n8n-workflow n8n-core
   ```

4. Create node file `MyNode.node.ts`:

```typescript
import {
  IExecuteFunctions,
  INodeExecutionData,
  INodeType,
  INodeTypeDescription,
} from 'n8n-workflow';

export class MyNode implements INodeType {
  description: INodeTypeDescription = {
    displayName: 'My Custom Node',
    name: 'myNode',
    group: ['transform'],
    version: 1,
    description: 'Does something custom',
    defaults: {
      name: 'My Node',
    },
    inputs: ['main'],
    outputs: ['main'],
    properties: [
      {
        displayName: 'API Key',
        name: 'apiKey',
        type: 'string',
        default: '',
        required: true,
        description: 'API key for the service',
      },
      {
        displayName: 'Operation',
        name: 'operation',
        type: 'options',
        options: [
          {
            name: 'Get Data',
            value: 'getData',
          },
        ],
        default: 'getData',
      },
    ],
  };

  async execute(this: IExecuteFunctions): Promise<INodeExecutionData[][]> {
    const items = this.getInputData();
    const returnData: INodeExecutionData[] = [];

    const apiKey = this.getNodeParameter('apiKey', 0) as string;
    const operation = this.getNodeParameter('operation', 0) as string;

    for (let i = 0; i < items.length; i++) {
      if (operation === 'getData') {
        // Custom logic here
        returnData.push({
          json: {
            message: 'Custom operation completed',
            apiKey,
          },
        });
      }
    }

    return [returnData];
  }
}
```

5. Build and link:
   ```bash
   npm run build
   npm link
   ```

6. Link to n8n:
   ```bash
   cd ~/.n8n/custom
   npm link n8n-nodes-mynode
   ```

7. Restart n8n

Your custom node now appears in the node list.

### Scaling n8n for Production

**Queue Mode Setup**:

Requirements:
- Redis for job queue

**Docker Compose with Queue Mode**:

```yaml
version: '3.8'

services:
  redis:
    image: redis:7-alpine
    restart: always
    volumes:
      - redis_data:/data

  postgres:
    image: postgres:15
    restart: always
    environment:
      POSTGRES_USER: n8n
      POSTGRES_PASSWORD: n8n_password
      POSTGRES_DB: n8n
    volumes:
      - postgres_data:/var/lib/postgresql/data

  n8n-main:
    image: n8nio/n8n:latest
    restart: always
    ports:
      - '5678:5678'
    environment:
      DB_TYPE: postgresdb
      DB_POSTGRESDB_HOST: postgres
      DB_POSTGRESDB_PORT: 5432
      DB_POSTGRESDB_DATABASE: n8n
      DB_POSTGRESDB_USER: n8n
      DB_POSTGRESDB_PASSWORD: n8n_password
      EXECUTIONS_MODE: queue
      QUEUE_BULL_REDIS_HOST: redis
      QUEUE_BULL_REDIS_PORT: 6379
      N8N_BASIC_AUTH_ACTIVE: 'true'
      N8N_BASIC_AUTH_USER: admin
      N8N_BASIC_AUTH_PASSWORD: changeme
    volumes:
      - n8n_data:/home/node/.n8n
    depends_on:
      - postgres
      - redis

  n8n-worker:
    image: n8nio/n8n:latest
    restart: always
    command: worker
    environment:
      DB_TYPE: postgresdb
      DB_POSTGRESDB_HOST: postgres
      DB_POSTGRESDB_PORT: 5432
      DB_POSTGRESDB_DATABASE: n8n
      DB_POSTGRESDB_USER: n8n
      DB_POSTGRESDB_PASSWORD: n8n_password
      EXECUTIONS_MODE: queue
      QUEUE_BULL_REDIS_HOST: redis
      QUEUE_BULL_REDIS_PORT: 6379
    volumes:
      - n8n_data:/home/node/.n8n
    depends_on:
      - postgres
      - redis
    deploy:
      replicas: 3

volumes:
  redis_data:
  postgres_data:
  n8n_data:
```

This configuration runs:
- 1 n8n main process (API + UI)
- 3 worker processes (execute workflows)
- Redis for job queue
- PostgreSQL for data storage

Workers can be scaled independently:
```bash
docker-compose up --scale n8n-worker=5 -d
```

### Deployment Strategies

**Option 1: VPS Deployment**

1. Provision Ubuntu 22.04 server
2. Install Docker and Docker Compose
3. Upload docker-compose.yml
4. Configure environment variables
5. Set up reverse proxy (Nginx):

```nginx
server {
    listen 80;
    server_name n8n.yourdomain.com;

    location / {
        proxy_pass http://localhost:5678;
        proxy_set_header Host $host;
        proxy_set_header X-Real-IP $remote_addr;
        proxy_set_header X-Forwarded-For $proxy_add_x_forwarded_for;
        proxy_set_header X-Forwarded-Proto $scheme;

        # WebSocket support
        proxy_http_version 1.1;
        proxy_set_header Upgrade $http_upgrade;
        proxy_set_header Connection "upgrade";
    }
}
```

6. Set up SSL with Let's Encrypt:
   ```bash
   sudo apt install certbot python3-certbot-nginx
   sudo certbot --nginx -d n8n.yourdomain.com
   ```

**Option 2: Kubernetes Deployment**

Use n8n Helm chart:

```bash
helm repo add n8n https://n8n.io/n8n-helm-chart/
helm install n8n n8n/n8n
```

**Option 3: Cloud Platforms**

Deploy to:
- Railway: Connect GitHub repo, auto-deploy
- Render: Import Docker image, configure environment
- DigitalOcean App Platform: Deploy via Docker
- AWS ECS/Fargate: Use container definitions

### Monitoring and Observability

**Enable Logging**:

Environment variables:
```bash
N8N_LOG_LEVEL=debug
N8N_LOG_OUTPUT=file
N8N_LOG_FILE_LOCATION=/var/log/n8n/
```

**Workflow Execution Monitoring**:

Create monitoring workflow:

1. **Add Schedule Trigger** (Every 5 minutes)
2. **Add HTTP Request Node** (Query n8n API)
   - Method: GET
   - URL: `http://localhost:5678/rest/executions`
   - Authentication: Basic Auth (n8n credentials)
3. **Add Function Node** (Check for Failures)
   ```javascript
   const executions = $json.data;
   const recentFailures = executions.filter(e => 
     e.finished === true && 
     e.stoppedAt &&
     e.data?.resultData?.error
   );

   return [{
     json: {
       failureCount: recentFailures.length,
       failures: recentFailures.map(e => ({
         workflowId: e.workflowId,
         error: e.data.resultData.error.message,
         time: e.stoppedAt
       }))
     }
   }];
   ```
4. **Add IF Node** (Check Threshold)
   - Condition: Number
   - Value 1: `{{ $json.failureCount }}`
   - Operation: Larger
   - Value 2: 0
5. **True Path: Add Slack Node** (Alert)

**Prometheus Metrics**:

n8n exposes metrics endpoint at `/metrics` when configured:

```bash
N8N_METRICS=true
N8N_METRICS_PREFIX=n8n_
```

Scrape with Prometheus:

```yaml
scrape_configs:
  - job_name: 'n8n'
    static_configs:
      - targets: ['localhost:5678']
```

Create Grafana dashboard to visualize:
- Workflow execution count
- Error rate
- Execution duration
- Active workflows

### Security Best Practices

**1. Authentication and Authorization**

Enable basic auth or use OAuth:
```bash
N8N_BASIC_AUTH_ACTIVE=true
N8N_BASIC_AUTH_USER=admin
N8N_BASIC_AUTH_PASSWORD=strong_password
```

**2. HTTPS Only**

Always use SSL/TLS in production:
```bash
N8N_PROTOCOL=https
N8N_SSL_KEY=/path/to/key.pem
N8N_SSL_CERT=/path/to/cert.pem
```

**3. Webhook Security**

Add authentication to webhooks:

1. Generate secret token
2. In webhook-receiving workflow, add IF node:
   ```
   {{ $json.headers.authorization }} === "Bearer YOUR_SECRET_TOKEN"
   ```
3. Reject unauthorized requests

**4. Credential Encryption**

Ensure encryption key is set:
```bash
N8N_ENCRYPTION_KEY=your-32-character-encryption-key
```

Store in secure location, never commit to version control.

**5. Network Isolation**

In Docker:
- Use custom network
- Don't expose PostgreSQL/Redis ports publicly
- Only expose n8n port via reverse proxy

**6. Regular Backups**

Backup PostgreSQL database:
```bash
docker exec postgres pg_dump -U n8n n8n > n8n_backup_$(date +%Y%m%d).sql
```

Backup workflow files:
```bash
tar -czf n8n_workflows_$(date +%Y%m%d).tar.gz ~/.n8n/workflows
```

Automate with cron:
```bash
0 2 * * * /path/to/backup_script.sh
```

### Testing Workflows

**Manual Testing**:
1. Use "Execute Workflow" button with test data
2. Pin data on nodes to test downstream logic
3. Check execution logs for errors

**Automated Testing**:

Create test workflow:

1. **Add Manual Trigger**
2. **Add Execute Workflow Node**
   - Workflow: Your workflow to test
   - Test data:
     ```json
     {
       "input1": "test value",
       "input2": 123
     }
     ```
3. **Add Function Node** (Validate Output)
   ```javascript
   const output = $json;

   const assertions = [
     { test: output.result !== undefined, message: "Result exists" },
     { test: output.status === "success", message: "Status is success" },
     { test: typeof output.data === "object", message: "Data is object" }
   ];

   const failures = assertions.filter(a => !a.test);

   if (failures.length > 0) {
     throw new Error(`Tests failed: ${failures.map(f => f.message).join(', ')}`);
   }

   return [{ json: { message: "All tests passed" } }];
   ```

Run this test workflow before deploying changes.

### Debugging Workflows

**Debugging Techniques**:

1. **Use Set Node to Inspect Data**
   - Add Set node after problematic node
   - Set all fields from `$json` to see structure

2. **Check Execution Data**
   - Click on node after execution
   - View Input/Output tabs
   - Examine JSON data structure

3. **Enable Debug Logging**
   - Add Function node with `console.log()`
   - Check n8n logs: `docker logs n8n`

4. **Test Expressions in Expression Editor**
   - Open expression editor (click expression field)
   - Test expressions against real data
   - Use Variable Selector to browse available data

5. **Isolate Problematic Nodes**
   - Disconnect node from workflow
   - Test independently with pinned data
   - Reconnect once working

**Common Issues and Solutions**:

**Issue**: Expression returns undefined

**Solution**: 
- Check data structure with Set node
- Verify property names (case-sensitive)
- Use optional chaining: `{{ $json.data?.property }}`

**Issue**: HTTP Request timeout

**Solution**:
- Increase timeout in node settings
- Enable "Continue On Fail"
- Add retry logic

**Issue**: Workflow executes but no data passed

**Solution**:
- Check if previous node returns empty array
- Verify node connections
- Ensure trigger node activates correctly

### Mini-Project 5: Multi-Channel Content Publisher

**Goal**: Create content once, publish to multiple platforms (WordPress, Twitter, LinkedIn, Telegram).

**Steps**:

1. **Add Webhook Trigger**
   - Path: publish-content
   - HTTP Method: POST

2. **Add Set Node** (Extract Content)
   - title: `{{ $json.body.title }}`
   - content: `{{ $json.body.content }}`
   - image_url: `{{ $json.body.image_url }}`
   - tags: `{{ $json.body.tags }}`

3. **Add HTTP Request Node** (Download Image)
   - Method: GET
   - URL: `{{ $json.image_url }}`
   - Response Format: File

4. **Add WordPress Node** (Create Post)
   - Operation: Create
   - Title: `{{ $node["Set"].json.title }}`
   - Content: `{{ $node["Set"].json.content }}`
   - Status: Publish

5. **Add Twitter Node** (Tweet)
   - Text: `{{ $node["Set"].json.title }} - {{ $node["Set"].json.content.substring(0, 200) }}...`
   - Media: Use binary data from HTTP Request

6. **Add LinkedIn Node** (Share)
   - Post: `{{ $node["Set"].json.title }}

{{ $node["Set"].json.content }}`

7. **Add Telegram Node** (Send Message)
   - Chat ID: Your channel ID
   - Text: `{{ $node["Set"].json.title }}

{{ $node["Set"].json.content }}`

8. **Add Function Node** (Collect Results)
   ```javascript
   return [{
     json: {
       status: "published",
       platforms: {
         wordpress: $node["WordPress"].json.id,
         twitter: $node["Twitter"].json.id,
         linkedin: $node["LinkedIn"].json.id,
         telegram: $node["Telegram"].json.message_id
       },
       timestamp: new Date().toISOString()
     }
   }];
   ```

9. **Add Webhook Response Node**
   - Response: `{{ $json }}`

**Test with curl**:

```bash
curl -X POST https://your-n8n.com/webhook/publish-content   -H "Content-Type: application/json"   -d '{
    "title": "My Blog Post",
    "content": "This is the content of my blog post...",
    "image_url": "https://example.com/image.jpg",
    "tags": ["automation", "n8n", "productivity"]
  }'
```

### Performance Optimization

**1. Batch Processing**

Instead of processing items one by one, batch them:

```javascript
const items = $input.all();
const batchSize = 10;
const batches = [];

for (let i = 0; i < items.length; i += batchSize) {
  batches.push(items.slice(i, i + batchSize));
}

// Process batches
const results = await Promise.all(
  batches.map(batch => processBatch(batch))
);

return results.flat();
```

**2. Parallel Execution**

Use Code node with Promise.all for parallel API calls:

```javascript
const axios = require('axios');

const promises = $input.all().map(item => 
  axios.get(`https://api.example.com/${item.json.id}`)
);

const results = await Promise.all(promises);

return results.map((response, index) => ({
  json: {
    ...$input.all()[index].json,
    apiData: response.data
  }
}));
```

**3. Caching**

Cache API responses to reduce external calls:

```javascript
const cache = $getWorkflowStaticData('node');
const cacheKey = `api_${$json.id}`;
const cacheExpiry = 3600000; // 1 hour in ms

if (cache[cacheKey] && cache[`${cacheKey}_time`] > Date.now()) {
  return [{ json: cache[cacheKey] }];
}

// Fetch from API
const response = await fetch(`https://api.example.com/${$json.id}`);
const data = await response.json();

cache[cacheKey] = data;
cache[`${cacheKey}_time`] = Date.now() + cacheExpiry;

return [{ json: data }];
```

**4. Limit Data Size**

Only select needed fields from databases:

```sql
SELECT id, name, email FROM users
-- Instead of SELECT * FROM users
```

**5. Use Webhooks Over Polling**

Prefer webhook triggers over schedule triggers that poll APIs.

### Version Control for Workflows

**Export Workflows**:

1. Settings > Export
2. Save as JSON
3. Commit to Git repository

**Import Workflows**:

1. New Workflow > Import from File
2. Select JSON file

**Automation Script for Backup**:

```bash
#!/bin/bash

# Export all workflows
curl -u admin:password http://localhost:5678/rest/workflows   -o workflows_backup_$(date +%Y%m%d).json

# Commit to Git
git add workflows_backup_*.json
git commit -m "Backup workflows $(date +%Y%m%d)"
git push origin main
```

Add to cron:
```bash
0 3 * * * /path/to/backup_workflows.sh
```

## Common Integration Patterns

### Gmail Integration

**Send Email**:

1. Create Gmail credentials (OAuth2)
2. Add Gmail node
3. Operation: Send
4. To: `{{ $json.recipient }}`
5. Subject: `{{ $json.subject }}`
6. Message: `{{ $json.body }}`

**Read Emails**:

1. Add Gmail Trigger node
2. Trigger On: Email Received
3. Label: INBOX
4. Process emails in workflow

### Slack Integration

**Send Message**:

1. Create Slack credentials (OAuth2 or Bot Token)
2. Add Slack node
3. Resource: Message
4. Operation: Post
5. Channel: Select or use ID
6. Text: `{{ $json.message }}`

**Advanced Slack Message**:

Use blocks for rich formatting:

```json
{
  "blocks": [
    {
      "type": "header",
      "text": {
        "type": "plain_text",
        "text": "{{ $json.title }}"
      }
    },
    {
      "type": "section",
      "text": {
        "type": "mrkdwn",
        "text": "{{ $json.description }}"
      }
    },
    {
      "type": "actions",
      "elements": [
        {
          "type": "button",
          "text": {
            "type": "plain_text",
            "text": "View Details"
          },
          "url": "{{ $json.url }}"
        }
      ]
    }
  ]
}
```

### Airtable Integration

**Add Record**:

1. Create Airtable credentials (API Key)
2. Add Airtable node
3. Operation: Append
4. Base: Select your base
5. Table: Select table
6. Fields:
   - Name: `{{ $json.name }}`
   - Email: `{{ $json.email }}`
   - Status: `{{ $json.status }}`

**Query Records**:

1. Operation: List
2. Formula: `{Status} = 'Active'`
3. Process results in next node

### Google Sheets Integration

**Append Row**:

1. Create Google Sheets credentials (OAuth2)
2. Add Google Sheets node
3. Operation: Append
4. Document: Select spreadsheet
5. Sheet: Sheet name
6. Columns:
   - A: `{{ $json.col1 }}`
   - B: `{{ $json.col2 }}`

**Read Rows**:

1. Operation: Get Many
2. Range: A1:Z1000
3. Returns array of rows

### Webhook Best Practices

**Secure Webhooks**:

1. Use HTTPS
2. Validate signature if provided by service
3. Implement IP whitelist
4. Use authentication headers

**Example Webhook Validation**:

```javascript
const crypto = require('crypto');

const signature = $json.headers['x-signature'];
const payload = JSON.stringify($json.body);
const secret = 'your-webhook-secret';

const expectedSignature = crypto
  .createHmac('sha256', secret)
  .update(payload)
  .digest('hex');

if (signature !== expectedSignature) {
  throw new Error('Invalid signature');
}

return [{
  json: {
    validated: true,
    data: $json.body
  }
}];
```

## Conclusion and Next Steps

You now have comprehensive knowledge of n8n from basic concepts to advanced production deployment. Here are recommended next steps:

**Practice Projects**:

1. Build a personal productivity dashboard that aggregates data from multiple sources
2. Create an automated customer support system using AI and ticket management
3. Develop a data pipeline that syncs data between multiple databases
4. Implement a monitoring system for your websites/APIs with alerting

**Resources**:

- Official Documentation: https://docs.n8n.io
- Community Forum: https://community.n8n.io
- Workflow Templates: https://n8n.io/workflows
- GitHub Repository: https://github.com/n8n-io/n8n
- YouTube Channel: n8n official channel

**Community Engagement**:

- Share your workflows on the forum
- Contribute to open-source n8n development
- Create custom nodes for specific use cases
- Help other users troubleshoot issues

**Continuous Learning**:

- Follow n8n blog for new features
- Experiment with new node integrations
- Study complex workflows shared by community
- Join n8n Discord for real-time discussions

By mastering n8n, you have gained a powerful tool for automation that can save hours of manual work, integrate disparate systems, and enable new capabilities in your personal or professional projects. Continue building, experimenting, and optimizing your workflows to maximize the value of automation.
