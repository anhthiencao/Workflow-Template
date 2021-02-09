# regwan_workflow

### API

| Method      | URI                | Description                    |
| :---       | :----             | :---                          |
| GET         | template/workflows | Return all current workflows   |

Respond body = 

```
{
  {
    "id": 1,
    "name": "Cisco workflow",
    "steps": [
      {
        "id": 1,
        "title": "Start",
        "activities": [
          {
            "id": 1,
            "direction": "typography",
            "title": "Introduction",
            "type": "text",
            "var":"in_intro",
            "args":"Start counting the progress."
          }
        ],
        "allow_change": true,
        "allow_return": true
      },
      {
        "id": 2,
        "title": "Preparation",
        "activities": [
          {
            "id": 1,
            "direction": "input",
            "title": "Hostname",
            "type": "text",
            "var":"in_hostname",
            "args":""
          },
          {
            "id": 2,
            "direction": "select",
            "title": "Type",
            "type": "text",
            "params": ["1", "2", "3"],
            "var":"in_type",
            "args":""
          },
          {
            "id": 3,
            "direction": "select",
            "title": "File",
            "type": "text",
            "params": ["Interfaces", "Routing", "Protocols", "Forwarding", "Policy"],
            "var":"in_file",
            "args":""
          },
          {
            "id": 4,
            "direction": "callback",
            "title": "Backup old config",
            "type": "text",
            "var":"old_config",
            "args":""
          }
        ],
        "allow_change": true,
        "allow_return": true
      },
      {
        "id": 3,
        "title": "Build Config",
        "activities": [
          {
            "id": 1,
            "direction": "callback",
            "title": "bgp_peer_last",
            "type": "text",
            "var":"in_bgp_peer_last",
            "args":"http://portal/api/v1/config/##in_hostname##/##in_type##/##in_file##"
          }
        ],
        "allow_change": true,
        "allow_return": true
      },
      {
        "id": 4,
        "title": "Prepare Router",
        "activities": [
          {
            "id": 1,
            "direction": "typography",
            "title": "Router",
            "type": "text",
            "var":"in_router",
            "args":"The prepare router progress"
          }
        ],
        "allow_change": true,
        "allow_return": true
      },
      {
        "id": 5,
        "title": "Perform Change",
        "activities": [
          {
            "id": 1,
            "direction": "typography",
            "title": "Change Device",
            "type": "text",
            "var":"in_change_device",
            "args":"Change the progress"
          }
        ],
        "allow_change": true,
        "allow_return": true
      }
    ]
  },
  "2_Juniper_workflow": {...
  },
  "3_name3": {...
  },
  "4_name4": {...
  },
  "5_name5": {...
  },
}
```
| Method      | URI                     | Description                  |
| :---       | :----                  | :---                        |
| GET         | template/workflows/:id  | Return workflow by id        |

Response body =

```
{
  "id": 1,
  "name": "Cisco workflow",
  "steps": [
    {
      "id": 1,
      "title": "Start",
      "activities": [
        {
          "id": 1,
          "direction": "typography",
          "title": "Introduction",
          "type": "text",
          "var":"in_intro",
          "args":"Start counting the progress."
        }
      ],
      "allow_change": true,
      "allow_return": true
    },
    {
      "id": 2,
      "title": "Preparation",
      "activities": [
        {
          "id": 1,
          "direction": "input",
          "title": "Hostname",
          "type": "text",
          "var":"in_hostname",
          "args":""
        },
        {
          "id": 2,
          "direction": "select",
          "title": "Type",
          "type": "text",
          "params": ["1", "2", "3"],
          "var":"in_type",
          "args":""
        },
        {
          "id": 3,
          "direction": "select",
          "title": "File",
          "type": "text",
          "params": ["Interfaces", "Routing", "Protocols", "Forwarding", "Policy"],
          "var":"in_file",
          "args":""
        },
        {
          "id": 4,
          "direction": "callback",
          "title": "Backup old config",
          "type": "text",
          "var":"old_config",
          "args":""
        }
      ],
      "allow_change": true,
      "allow_return": true
    },
    {
      "id": 3,
      "title": "Build Config",
      "activities": [
        {
          "id": 1,
          "direction": "callback",
          "title": "bgp_peer_last",
          "type": "text",
          "var":"in_bgp_peer_last",
          "args":"http://portal/api/v1/config/##in_hostname##/##in_type##/##in_file##"
        }
      ],
      "allow_change": true,
      "allow_return": true
    },
    {
      "id": 4,
      "title": "Prepare Router",
      "activities": [
        {
          "id": 1,
          "direction": "typography",
          "title": "Router",
          "type": "text",
          "var":"in_router",
          "args":"The prepare router progress"
        }
      ],
      "allow_change": true,
      "allow_return": true
    },
    {
      "id": 5,
      "title": "Perform Change",
      "activities": [
        {
          "id": 1,
          "direction": "typography",
          "title": "Change Device",
          "type": "text",
          "var":"in_change_device",
          "args":"Change the progress"
        }
      ],
      "allow_change": true,
      "allow_return": true
    }
  ]
}
```
| Method      | URI                     | Description                  |
| :---       | :----                  | :---                        |
| POST        | template/workflows/new  | Create new workflow          | 

Request body = 
```
{
  "name": "Cisco workflow",
  "steps": [
    {
      "title": "Start",
      "activities": [
        {
          "direction": "typography",
          "title": "Introduction",
          "type": "text",
          "var": "in_intro",
          "args": "Start counting the progress."
        }
      ],
      "allow_change": true,
      "allow_return": true
    },
    {
      "title": "Preparation",
      "activities": [
        {
          "direction": "input",
          "title": "Hostname",
          "type": "text",
          "var": "in_hostname",
          "args": ""
        },
        {
          "direction": "select",
          "title": "Type",
          "type": "text",
          "params": ["1", "2", "3"],
          "var": "in_type",
          "args": ""
        },
        {
          "direction": "select",
          "title": "File",
          "type": "text",
          "params": [
            "Interfaces",
            "Routing",
            "Protocols",
            "Forwarding",
            "Policy"
          ],
          "var": "in_file",
          "args": ""
        },
        {
          "direction": "callback",
          "title": "Backup old config",
          "type": "text",
          "var": "old_config",
          "args": "http://regwan01.wentdark.de/regwan/configs/by-name/##in_hostname##"
        }
      ],
      "allow_change": true,
      "allow_return": true
    },
    {
      "title": "Build Config",
      "activities": [
        {
          "direction": "callback",
          "title": "bgp_peer_last",
          "type": "text",
          "var": "in_bgp_peer_last",
          "args": "http://192.168.1.74/api/v1/config/##in_hostname##/##in_type##/##in_file##"
        }
      ],
      "allow_change": true,
      "allow_return": true
    },
    {
      "title": "Prepare Router",
      "activities": [
        {
          "direction": "typography",
          "title": "Router",
          "type": "text",
          "var": "in_router",
          "args": "The prepare router progress"
        }
      ],
      "allow_change": true,
      "allow_return": true
    },
    {
      "title": "Perform Change",
      "activities": [
        {
          "direction": "typography",
          "title": "Change Device",
          "type": "text",
          "var": "in_change_device",
          "args": "Change the progress"
        }
      ],
      "allow_change": true,
      "allow_return": true
    }
  ]
}
```

The same json content as `template/workflows/new`

| Method | URI                   | Description                  |
| :---  | :----                | :---                        |
| PUT    | template/workflows/:id| Edit and update content of workflow by id, return new written item|

| Method | URI                   | Description                  |
| :---  | :----                | :---                        |
| DELETE | template/workflows/:id| Delete workflow by id, return status code|

| Method | URI                           | Description                  |
| :---  | :----                       | :---                        |
| PUT    | template/workflows/recover/:id| Return deleted workflow by ID|

| Method | URI                           | Description                  |
| :---  | :----                        | :---                        |
| GET    | template/workflows/delete     | Return all deleted workflows |






