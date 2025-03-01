![GenI-Banner](https://github.com/genilab-fau/genial-fau.github.io/blob/8f1a2d3523f879e1082918c7bba19553cb6e7212/images/geni-lab-banner.png?raw=true)

# COT6930-001 – Gen AI in Software Development Lifecycles

A comparative analysis of various prompt engineering methodologies for extracting comprehensive software requirements using LLMs.

- Authors: Caleb Waymeyer
- Academic Supervisor: Dr. Fernando Koch

# Research Question

How can different prompt engineering techniques optimize the quality, completeness, and efficiency of automated requirements analysis for specialized software solutions?

## Arguments

#### What is already known about this topic

-   Large Language Models (LLMs) can be leveraged to generate initial requirements documentation, saving significant time in the software development process.
    
-   The quality of LLM outputs is highly dependent on the prompt engineering techniques employed.
    
-   Chain-of-thought prompting can improve reasoning capabilities in complex technical domains.
    
-   Few-Shot learning with carefully selected examples can guide models toward more accurate and domain-specific outputs.
    
-   The challenge of maintaining consistency in requirements generated through AI systems.
    
-   The possibility of using multi-step prompting techniques to refine and enhance initial requirements.
    

#### What this research is exploring

-   Carious prompt engineering techniques (Role-Assisted, Self-Consistency, Meta, and Chain-of-Thought) to generate requirements for a Physics Discord Bot.
    
-   Building a comparative framework to evaluate the effectiveness of each technique in terms of output quality, completeness, and processing time.
    
-  Exploring how model parameters (temperature, context window, prediction length) affect the requirements generation process.
    
-   Investigating how prompt structure and complexity influence the comprehensiveness of generated requirements.
    

#### Implications for Practice

-   It will be easier to automate the initial phases of requirements gathering for specialized software projects.
    
-   It will optimize the software development lifecycle by reducing time spent on preliminary requirement drafting.
    
-   We will better understand how to construct prompts that extract domain-specific technical requirements with higher accuracy.
    
-   Development teams can leverage these techniques to create more robust software specifications with reduced human effort.
    

# Research Method

Our research methodology involved a systematic comparison of four different prompt engineering techniques applied to the same use case - generating requirements for a Physics Discord Bot:

1.  Role-Assisted Prompting: Assigning the model the role of a requirements engineer to provide expert-level requirements.
    
2.  Self-Consistency: Presenting multiple attempts at requirement analysis and extracting consistent patterns to arrive at a more reliable set of requirements.
    
3.  Meta-Prompting: A refined prompt explicitly structuring categories of requirements (core features, user interaction, integrations, performance, security) to direct the model's output organization.
    
4.  Chain-of-Thought Prompting: Step-by-step reasoning before arriving at complete requirement specifications, encouraging the model to break down complex requirements into logical components.

For each technique, I maintained consistent use of the llama3.2 model through the "ollama" platform, varying parameters such as temperature, context window size, and prediction length to optimize outputs. I measured both qualitative aspects (completeness, relevance, organization) and quantitative metrics (processing time, token count).

# Results

### Output Comprehensiveness

-   Chain-of-Thought: Most detailed requirements (41.311s processing time), generating a comprehensive hierarchical structure with thorough reasoning and data.
    
-   Meta-Prompting: Good balance of detail and structure (25.581s), with clear categorization of requirements.
    
-   Self-Consistency: Precise and analytical requirements (22.437s), focusing on consistency and accuracy.
    
-   Role-Assisted: Fine but shorter answer (8.943s), suitable for basic requirements.
    

### Processing Efficiency

-   Role-Assisted: Most efficient in terms of time (8.943s), though with less comprehensive output.
    
-   Self-Consistency and Meta-Prompting: Moderate processing times (22.437s and 25.581s respectively), providing a good trade-off between time and detail.
    
-   Chain-of-Thought: Least efficient (41.311s), but delivered the most in-depth requirements.

| `prompt method`    | `time`   |
| ---------------- | ------ |
| meta             | 25.581 |
| role-assisted    | 8.943  |
| self-consistency | 22.437 |
| chain-of-thought | 41.311 |
    

### Parameter Impact

From a separate experiment with a simple prompt, I observed ("quality" metric was determined by an LLM assessment of effectiveness of answer):
| `temperature` | `num_ctx` | `num_predict` | `time`   | `quality` |
| ----------- | ------- | ----------- | ------ | ------- |
| 0.1         | 50      | 50          | 9.655  | 9       |
| 0.1         | 50      | 100         | 6.829  | 9       |
| 0.1         | 500     | 50          | 7.063  | 8.5     |
| 0.1         | 500     | 100         | 6.824  | 8.5     |
| 0.5         | 50      | 50          | 2.787  | 7       |
| 0.5         | 50      | 100         | 6.903  | 9       |
| 0.5         | 500     | 50          | 9.700  | 10      |
| 0.5         | 500     | 100         | 8.302  | 8.5     |
| 1           | 50      | 50          | 10.491 | 9       |
| 1           | 50      | 100         | 9.342  | 10      |
| 1           | 500     | 50          | 8.775  | 10      |
| 1           | 500     | 100         | 7.224  | 9.5     |

-   Lower temperature settings (0.1) generally led to higher quality outputs.
    
-   Higher temperature (0.5) with smaller context sizes could lead to faster processing but lower quality.
    
-   Increasing the prediction length from 50 to 100 tokens sometimes decreased processing time, suggesting that generating more tokens could be more efficient in certain cases.
    

This indicates that parameter tuning is crucial for optimizing both the quality and efficiency of the model's outputs, and similar considerations were applied when using the different prompt engineering techniques.

### Quality Assessment

-   Chain-of-Thought and Meta-Prompting techniques generated the most comprehensive and detailed requirements.
    
-   Self-Consistency provided precise and consistent requirements.
    
-   Role-Assisted produced acceptable but less detailed requirements.
    

# Further Research

Future research directions could significantly expand on the foundations established in this study:

1.  Combined Pipelines: Develop combined pipelines that leverage multiple prompt engineering techniques sequentially to maximize both efficiency and quality.
    
2.  Domain-Specific Techniques: Extend this research to other specialized domains to determine if certain prompt engineering techniques work better for specific types of requirements.
    
3.  Automated Prompt Generation: Create automated systems that generate optimal prompt templates based on the specific requirements domain and desired output format.
    
4.  Requirement Validation: Implement techniques to validate the accuracy and completeness of AI-generated requirements against industry standards and human expert assessments.
    
5.  Model Comparison: Compare how different LLM architectures respond to the same prompt engineering techniques.
    
6.  Human-AI Collaboration: Investigate interactive prompt engineering systems where human input refines the requirements in real-time based on AI-generated suggestions.

