# Snowplow Custom Schemas

This repository contains custom JSON schemas for Snowplow analytics tracking. These schemas define the structure of custom contexts that are sent with Snowplow events.

## Schema Structure

The schemas follow the Iglu repository structure:

```
schemas/
└── com.example/
    ├── legacy_ids/
    │   └── jsonschema/
    │       └── 1-0-0/
    │           └── schema.json
    ├── experiment_assignments/
    │   └── jsonschema/
    │       └── 1-0-0/
    │           └── schema.json
    └── page_context/
        └── jsonschema/
            └── 1-0-0/
                └── schema.json
```

## Available Schemas

### Legacy IDs (`com.example/legacy_ids/jsonschema/1-0-0`)

This schema defines the structure for tracking legacy user and session IDs.

### Experiment Assignments (`com.example/experiment_assignments/jsonschema/1-0-0`)

This schema defines the structure for tracking A/B testing experiment assignments.

### Page Context (`com.example/page_context/jsonschema/1-0-0`)

This schema defines the structure for tracking page context information.

## Usage

These schemas are used in the Shopify Snowplow integration to track custom contexts with events.

Example usage in JavaScript:

```javascript
window.snowplow("addGlobalContexts", [
  {
    schema: "iglu:com.example/legacy_ids/jsonschema/1-0-0",
    data: {
      "uid-legacy": userId,
      "sid-legacy": sessionId,
    },
  },
]);
```

## Schema Validation

To validate your events against these schemas, you can use the Iglu schema validator or the Snowplow schema validation functionality in your Snowplow pipeline.
