Rules
OpenAI Text Generation Rules
API
TG-001 — Use the Responses API for new projects
* If you're building a new AI application, use the Responses API instead of older APIs.
TG-002 — Use the Responses API with reasoning models
* If you're using a reasoning model, use the Responses API.
TG-003 — Don't assume where the model's answer is
* The response can contain text, tool calls, reasoning and more.
* Don't hardcode where you expect the answer to be.
TG-004 — Use output_text when you only need the answer
* If you only care about the generated text, use the SDK's output_text helper instead of parsing the response yourself.

Models
TG-005 — Pin the model version in production
* Don't use a model alias that can change over time.
* Use a specific model version so your application behaves consistently.
TG-006 — Test before upgrading models
* Before switching to a newer model, make sure your prompts still work correctly.

Instructions
TG-007 — Put important behaviour in the instructions
* Use the instructions field to tell the model how it should behave.
TG-008 — Instructions take priority
* Put rules, behaviour and constraints in the instructions because they have the highest priority.
TG-009 — Send instructions with every request
* Don't assume the model remembers previous instructions.
* Include them whenever you need them.

Prompt Writing
TG-010 — Clearly describe the task
* Tell the model exactly what you want it to do.
TG-011 — Adjust prompts for different models
* A prompt that works well on one model may need changes for another.
TG-012 — Use examples when they help
* If examples improve the output, include them in your prompt.

Prompt Management
TG-013 — Store prompts in code
* Keep prompts in your codebase so they can be version controlled.
TG-014 — Keep prompts close to the feature that uses them
* Store prompts with the code they belong to instead of in random documents.

Inputs
TG-015 — Use structured inputs when possible
* Prefer structured inputs over building one long prompt string.

Testing
TG-016 — Create test examples
* Prepare representative examples to test your prompts.
TG-017 — Test prompts before shipping
* Don't deploy prompt changes without testing them first.
TG-018 — Add automated prompt tests
* Include prompts in your automated test suite.
TG-019 — Run evaluations after prompt changes
* Check whether the new prompt performs better before releasing it.

Deployment
TG-020 — Deploy prompts like code
* Release prompt changes using your normal deployment process.
TG-021 — Roll out prompt changes gradually
* Use feature flags or configuration to release prompts safely.
TG-022 — Monitor prompts after deployment
* Watch how prompts perform in production and look for issues.
OpenAI Structured Outputs Rules
Choosing Structured Outputs
SO-001 — Use Structured Outputs when you need structured responses
* Use Structured Outputs when your application expects a response that matches a predefined schema.
SO-002 — Use Function Calling for tools
* If the model needs to call APIs, databases, functions or interact with your application, use Function Calling.
SO-003 — Use text.format for structured responses
* If the model is replying directly to the user with structured data, use Structured Outputs via text.format.

JSON Mode
SO-004 — Prefer Structured Outputs over JSON Mode
* Use Structured Outputs whenever your use case supports it.
SO-005 — Remember the difference
* JSON Mode guarantees valid JSON.
* Structured Outputs guarantees valid JSON that matches your schema.
SO-006 — Check model support
* Structured Outputs using json_schema only works on supported model versions.
SO-007 — If using JSON Mode, explicitly ask for JSON
* Your prompt must explicitly tell the model to generate JSON.
SO-008 — Don't expect JSON Mode to enforce your schema
* JSON Mode only guarantees valid JSON, not the structure of that JSON.
SO-009 — Handle JSON Mode edge cases
* Your application must detect incomplete or invalid JSON responses.

Schema Design
SO-010 — Define a schema before making the request
* Create your schema first, then pass it to the API.
SO-011 — Use JSON Schema
* Define structured responses using JSON Schema.
SO-012 — Use Pydantic or Zod when possible
* Prefer native SDK support instead of manually writing JSON Schema.
SO-013 — Prevent schema and code from drifting
* Keep your schema and application types in sync.
* Generate one from the other or enforce this in CI.

Handling User Input
SO-014 — Handle incompatible input
* Tell the model what to return when the user's input doesn't match the task.
SO-015 — Expect hallucinations on unrelated input
* Without instructions, the model may hallucinate values to satisfy the schema.

Handling Responses
SO-016 — Handle refusals
* Check whether the model returned a refusal instead of structured data.
SO-017 — Don't assume refusals follow your schema
* A refusal has its own response field and may not match your schema.
SO-018 — Handle mistakes
* If the model makes mistakes:
    * improve the instructions,
    * provide examples,
    * or split the task into smaller subtasks.

Streaming
SO-019 — Use streaming when appropriate
* Use streaming if you want to process structured data before the full response finishes.
SO-020 — Prefer the SDK for streaming
* Let the SDK handle streaming Structured Outputs instead of implementing it yourself.

Supported Schemas
SO-021 — Use supported JSON Schema features
* Structured Outputs only supports a subset of JSON Schema.
SO-022 — Use supported data types
* Supported types include:
    * String
    * Number
    * Integer
    * Boolean
    * Object
    * Array
    * Enum
    * anyOf
SO-023 — Use supported validation constraints
* Only use schema constraints that Structured Outputs supports.
SO-024 — Recursive schemas are supported
* You can use recursive JSON Schemas when needed.

Benefits
These aren't implementation rules, but they are explicit claims from the documentation:
SO-025
* Structured Outputs provides reliable type safety.
SO-026
* Structured Outputs makes safety refusals detectable.
SO-027
* Structured Outputs reduces the need for prompt engineering to enforce output formatting.

I deliberately did not include things like:
* "Use additionalProperties: false everywhere."
* "Make all fields required."
* "Root must be an object."
Although those appear in schema examples, the documentation excerpts you've provided don't present them as universal rules—they're shown in examples or in the supported schema section. I don't want to promote example patterns into mandatory rules unless the documentation explicitly states them. That keeps the inventory faithful to the source.



OpenAI Structured Outputs Rules
Choosing Structured Outputs
SO-001 — Use Structured Outputs when you need structured responses
* Use Structured Outputs when your application expects a response that matches a predefined schema.
SO-002 — Use Function Calling for tools
* If the model needs to call APIs, databases, functions or interact with your application, use Function Calling.
SO-003 — Use text.format for structured responses
* If the model is replying directly to the user with structured data, use Structured Outputs via text.format.

JSON Mode
SO-004 — Prefer Structured Outputs over JSON Mode
* Use Structured Outputs whenever your use case supports it.
SO-005 — Remember the difference
* JSON Mode guarantees valid JSON.
* Structured Outputs guarantees valid JSON that matches your schema.
SO-006 — Check model support
* Structured Outputs using json_schema only works on supported model versions.
SO-007 — If using JSON Mode, explicitly ask for JSON
* Your prompt must explicitly tell the model to generate JSON.
SO-008 — Don't expect JSON Mode to enforce your schema
* JSON Mode only guarantees valid JSON, not the structure of that JSON.
SO-009 — Handle JSON Mode edge cases
* Your application must detect incomplete or invalid JSON responses.

Schema Design
SO-010 — Define a schema before making the request
* Create your schema first, then pass it to the API.
SO-011 — Use JSON Schema
* Define structured responses using JSON Schema.
SO-012 — Use Pydantic or Zod when possible
* Prefer native SDK support instead of manually writing JSON Schema.
SO-013 — Prevent schema and code from drifting
* Keep your schema and application types in sync.
* Generate one from the other or enforce this in CI.

Handling User Input
SO-014 — Handle incompatible input
* Tell the model what to return when the user's input doesn't match the task.
SO-015 — Expect hallucinations on unrelated input
* Without instructions, the model may hallucinate values to satisfy the schema.

Handling Responses
SO-016 — Handle refusals
* Check whether the model returned a refusal instead of structured data.
SO-017 — Don't assume refusals follow your schema
* A refusal has its own response field and may not match your schema.
SO-018 — Handle mistakes
* If the model makes mistakes:
    * improve the instructions,
    * provide examples,
    * or split the task into smaller subtasks.

Streaming
SO-019 — Use streaming when appropriate
* Use streaming if you want to process structured data before the full response finishes.
SO-020 — Prefer the SDK for streaming
* Let the SDK handle streaming Structured Outputs instead of implementing it yourself.

Supported Schemas
SO-021 — Use supported JSON Schema features
* Structured Outputs only supports a subset of JSON Schema.
SO-022 — Use supported data types
* Supported types include:
    * String
    * Number
    * Integer
    * Boolean
    * Object
    * Array
    * Enum
    * anyOf
SO-023 — Use supported validation constraints
* Only use schema constraints that Structured Outputs supports.
SO-024 — Recursive schemas are supported
* You can use recursive JSON Schemas when needed.

Benefits
These aren't implementation rules, but they are explicit claims from the documentation:
SO-025
* Structured Outputs provides reliable type safety.
SO-026
* Structured Outputs makes safety refusals detectable.
SO-027
* Structured Outputs reduces the need for prompt engineering to enforce output formatting.

I deliberately did not include things like:
* "Use additionalProperties: false everywhere."
* "Make all fields required."
* "Root must be an object."
Although those appear in schema examples, the documentation excerpts you've provided don't present them as universal rules—they're shown in examples or in the supported schema section. I don't want to promote example patterns into mandatory rules unless the documentation explicitly states them. That keeps the inventory faithful to the source.


next

Great. Here's Part 3 – Instructor.
These are only the explicit capabilities and recommendations described in the Instructor documentation—not my interpretations.

Instructor Rules
Provider
INS-001 — Use from_provider() to create clients
* Use from_provider() to work with supported LLM providers through a single interface.
INS-002 — Use the same interface across providers
* Switch between OpenAI, Anthropic, Google, Ollama and other supported providers without changing your extraction code.
INS-003 — Use synchronous or asynchronous clients
* from_provider() supports both synchronous and asynchronous usage.

Response Models
INS-004 — Define a response model
* Define the structure you expect using a Pydantic model.
INS-005 — Use typed fields
* Define field types so extracted data is type-safe.
INS-006 — Use nested models when needed
* Build more complex response structures using nested Pydantic models.
INS-007 — Use enums for fixed values
* Use enums when a field should only contain predefined values.
INS-008 — Use optional fields when data may be missing
* Mark fields as optional when they are not always expected.

Validation
INS-009 — Validate extracted data
* Use Pydantic validation to verify the model output.
INS-010 — Use custom validators
* Add your own validation rules when built-in type validation isn't enough.
INS-011 — Let Instructor retry validation failures
* Use the built-in retry mechanism when validation fails.

Extraction
INS-012 — Extract structured data directly
* Return structured objects instead of manually parsing text responses.
INS-013 — Use the response model as the contract
* Pass the response model to Instructor so it knows the structure to generate.

Streaming
INS-014 — Stream partial responses
* Process structured output as it is generated instead of waiting for the complete response.
INS-015 — Stream lists of objects
* Stream collections of structured objects when appropriate.

Type Safety
INS-016 — Use typed responses
* Work with typed Python objects instead of raw JSON.
INS-017 — Take advantage of IDE type support
* Use typed models to benefit from autocomplete and type checking.

Multi-Provider Support
INS-018 — Reuse the same extraction code
* Keep the extraction logic the same when switching providers.
INS-019 — Use supported providers
* Instructor supports multiple commercial and open-source LLM providers through a common interface.













