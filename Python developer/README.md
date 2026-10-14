# MDPI Senior Python Backend Engineer — Take-Home Assessment

**Position:** [Backend Engineer (Python)](https://careers.srb.mdpi.com/jobs/8331526-backend-engineer-python)
**Project:** Scientific Paper Similarity Service for MDPI Pulse
**Deadline:** 7 calendar days after receiving the assignment
**Expected effort:** no more than approximately 8 focused hours

## Context

MDPI Pulse works with scientific content and data pipelines to support more relevant communication with the academic community.

Your task is to build a small Python backend that:

1. retrieves scientific papers from arXiv;
2. generates and stores vector embeddings for those papers;
3. accepts a new paper or manuscript text;
4. returns the most similar papers from the indexed collection.

The assignment is intentionally open-ended. We want to understand how you interpret the problem, structure the application, select the appropriate technologies, and explain your decisions.

Focus on a complete and reliable core workflow rather than the number of features implemented.

## AI tools

You may use AI assistants during the assignment.

You remain responsible for the submitted solution and should be able to explain, modify, and troubleshoot every part of the code during the technical interview.

In the README, briefly mention:

- which AI tools you used;
- what you used them for;
- how you reviewed or validated their output.

The use of AI will not be evaluated negatively. We are interested in how you apply engineering judgment to AI-assisted work.

---

## Requirements

### 1. arXiv ingestion

Implement a process that retrieves scientific papers from the arXiv API and adds them to the application.

The implementation should:

- support a documented query or selection mechanism;
- ingest at least 30 papers for demonstration purposes;
- collect enough metadata to identify and display each paper;
- use the title and abstract as the minimum searchable content;
- avoid creating duplicate records when the same paper is processed more than once;
- handle external API failures in a reasonable way.

Processing arXiv metadata and abstracts is sufficient. Downloading and parsing complete PDF files is not required.

The ingestion process may run through a command, script, startup task, background process, or another approach. Choose an approach and explain why it is appropriate.

### 2. Embeddings and persistence

Generate an embedding for each indexed arXiv paper and store it persistently.

You are free to choose the embedding method, vector storage, similarity metric, and persistence strategy. We expect these choices to be explained in the README or architecture documentation.

The stored index must survive an application restart.

Your documentation should briefly explain:

- why you selected the embedding approach;
- why you selected the storage solution;
- how the text used for embedding is constructed;
- how similarity scores should be interpreted;
- any relevant limitations or trade-offs.

The project should be reviewable without requiring the reviewer to purchase access to a third-party service. If the solution depends on external credentials, document the setup clearly and provide a practical way to run the tests without them.

### 3. Submit a paper

Implement the following endpoint:

```http
POST /api/v1/papers
Content-Type: application/json
```

The endpoint accepts a new paper or manuscript that will be compared with the indexed arXiv collection.

Example request:

```json
{
  "title": "Optional manuscript title",
  "text": "The abstract or manuscript text to be compared with indexed papers."
}
```

The application should:

- validate the request;
- generate an embedding for the submitted text;
- persist the submitted paper;
- return a stable identifier that can be used in the similarity endpoint.

Example response:

```json
{
  "id": "paper-123",
  "status": "created"
}
```

The exact request and response schemas are your decision, provided that they are documented and support the required workflow.

### 4. Retrieve similar papers

Implement the following endpoint:

```http
GET /api/v1/posts/:id/similar
```

The `:id` identifies the paper previously created through `POST /api/v1/papers`.

The endpoint should:

- retrieve the stored embedding for the submitted paper;
- perform a vector similarity search against the indexed arXiv papers;
- return a ranked list of similar papers;
- include the similarity score and enough metadata to identify each result;
- support a configurable result limit;
- return appropriate responses for invalid or unknown identifiers.

Example response:

```json
{
  "paper_id": "paper-123",
  "matches": [
    {
      "arxiv_id": "2401.12345",
      "title": "Example scientific paper",
      "authors": ["First Author", "Second Author"],
      "url": "https://arxiv.org/abs/2401.12345",
      "score": 0.91
    }
  ]
}
```

The exact response schema is your decision. Results must be ordered consistently according to the selected similarity metric.

### 5. API behaviour

The API should:

- use meaningful HTTP status codes;
- validate incoming data;
- provide understandable error responses;
- expose basic application logs;
- include generated API documentation or equivalent usage documentation.

A simple health endpoint is recommended but not required.

### 6. Code quality

The solution should demonstrate professional Python engineering practices appropriate for a senior backend role.

We expect:

- type-annotated and readable Python code;
- clear separation of responsibilities;
- explicit configuration management;
- appropriate error handling;
- reproducible dependency management;
- no credentials or secrets committed to the repository;
- reasonable linting and formatting standards.

The project structure, libraries, frameworks, and development tools are intentionally left to you.

### 7. Testing

Include automated tests for the most important parts of the solution.

Tests should cover the core workflow and should not depend on the live availability of arXiv or paid external services.

We do not require a specific coverage percentage. Choose what to test based on risk and document any important test limitations.

### 8. Documentation and execution

The repository README should contain everything needed for another engineer to understand and run the project, including:

- prerequisites;
- installation and startup instructions;
- configuration;
- how to ingest arXiv papers;
- how to run the API;
- example requests for the required endpoints;
- how to run the tests;
- a short architecture overview;
- the main technical decisions and trade-offs;
- known limitations;
- a short note about AI tool usage.

The project should run locally using clearly documented commands. Containerization and CI are welcome, but they are not required for a complete submission.

---

## Scope guidance

The following are not required:

- a frontend or graphical interface;
- a conversational or generative AI layer;
- full-text PDF extraction;
- authentication or user management;
- cloud deployment;
- orchestration infrastructure;
- processing a production-scale arXiv dataset.

If you finish the core workflow early, you may add improvements that you believe make the service more reliable, scalable, observable, or useful. Select them based on your own judgment and explain why you considered them valuable.

## Expected deliverables

The submitted repository should include:

1. the working Python application;
2. arXiv ingestion;
3. persistent embeddings and vector similarity search;
4. the two required API endpoints;
5. automated tests;
6. setup and architecture documentation;
7. a readable Git history.

A focused implementation that works consistently is preferred over a large solution with unfinished features.

## Submission process

1. Create a GitHub repository for your solution. It may be public or private.
2. If it is private, add the GitHub accounts provided by MDPI as collaborators with read access.
3. Push the version you want us to review to the default branch.
4. Send the repository URL to your MDPI contact before the deadline.
5. Include any setup notes required by the reviewers, but do not send passwords or private API keys.

Please do not rewrite or force-push the submitted history after the deadline unless requested by MDPI.

## Technical interview

After reviewing the submission, selected candidates will be invited to a technical interview based on their implementation.

During the interview, you may be asked to walk through the solution, explain your decisions, discuss limitations or production considerations, and make or describe a small change to the code.

We do not expect a perfect production system. We expect a working solution, sound engineering judgment, and a clear understanding of the code you submit.
