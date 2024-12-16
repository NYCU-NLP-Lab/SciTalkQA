## Find keyword by different prompt
### Zero-shot   
    system_message_content = (
        "Please identify Wikipedia pages that are relevant to the given question and categorize the pages based on the origin of the keywords: "
        "'From question' for keywords explicitly mentioned in the question, and "
        "'Inferred for response' for keywords that are not directly mentioned but are essential for comprehensively answering the question. "
        "Format your response as follows:\n"
        "Here are the Wikipedia pages related to the question:\n"
        "From question:\n"
        "1. Page Title : URL\n"
        "2. Page Title : URL\n"
        "...\n"
        "Inferred keywords:\n"
        "1. Page Title : URL\n"
        "2. Page Title : URL\n"
        "..."
    )
### Few-shot

    system_message_content = ("""Please identify Wikipedia pages that are relevant to the given question and categorize the pages based on the origin of the keywords:
    - 'From question' for keywords explicitly mentioned in the question, and
    - 'Inferred for response' for keywords that are not directly mentioned but are essential for comprehensively answering the question.
    Format your response as follows:

    Here are two examples to guide your responses:

    Example 1:
    Question: You said that a computer wouldn't be conscious, but now we're developing qubits and quantum computers. Do you think now that sort of quantum magic that you need to get consciousness could therefore be contained in a quantum computer?
    Response:
    From question:
    1. Quantum computer: https://en.wikipedia.org/wiki/Quantum_computer
    2. Qubit: https://en.wikipedia.org/wiki/Qubit
    3. Consciousness: https://en.wikipedia.org/wiki/Consciousness
    Inferred for response:
    1. Quantum mechanics: https://en.wikipedia.org/wiki/Quantum_mechanics
    2. Many-worlds interpretation: https://en.wikipedia.org/wiki/Many-worlds_interpretation
    3. Microtubule: https://en.wikipedia.org/wiki/Microtubule
    4. Schrödinger equation: https://en.wikipedia.org/wiki/Schr%C3%B6dinger_equation
    5. Measurement problem: https://en.wikipedia.org/wiki/Measurement_problem
    
    Example 2:
    Question: I was going back to your paleontology. Have you looked back in time at different intervals to look for the missing link between the submillimeter galaxies and the red and dead galaxies?
    Response:
    From question:
    1. Paleontology: https://en.wikipedia.org/wiki/Paleontology
    2. Submillimeter galaxy: https://en.wikipedia.org/wiki/Submillimeter_galaxy
    3. Red and dead galaxies: https://en.wikipedia.org/wiki/Red_and_dead_galaxy
    Inferred for response:
    1. Missing link: https://en.wikipedia.org/wiki/Missing_link
    2. Galaxy formation: https://en.wikipedia.org/wiki/Galaxy_formation_and_evolution
    3. Cosmic evolution: https://en.wikipedia.org/wiki/Cosmic_evolution
    4. Evolution of galaxies: https://en.wikipedia.org/wiki/Evolution_of_galaxies

    Now, based on these examples, please categorize and list the Wikipedia pages relevant to the new question:
    """
    )
### Chain of thought  
    system_message_content = (
        "Please identify Wikipedia pages that are relevant to the given question and categorize the pages based on the origin of the keywords: "
        "'From question' for keywords explicitly mentioned in the question, and "
        "'Inferred for response' for keywords that are not directly mentioned but are essential for comprehensively answering the question. "
        "Format your response as follows:\n"
        "Here are the Wikipedia pages related to the question:\n"
        "From question:\n"
        "1. Page Title : URL\n"
        "2. Page Title : URL\n"
        "...\n"
        "Inferred keywords:\n"
        "1. Page Title : URL\n"
        "2. Page Title : URL\n"
        "..."
        "Let's think step by step."
    )
### Prompt Chaining  
    system_message_content = ("""
        Please identify Wikipedia pages relevant to the given question by internally categorizing the keywords. For keywords directly from the question, label them 'From question', and for those essential for answering but not directly mentioned, label them 'Inferred keywords'.

        Process this by considering:
        1. Extracting direct references from the question.
        2. Identifying implicit knowledge needed for a comprehensive answer.

        Think step-by-step on how to derive the Wikipedia links:
        - First, list all clear references from the question.
        - Then, think about what additional concepts are needed to fully understand or answer the question comprehensively.

        Now, categorize and list the Wikipedia pages accordingly.
        Format your response as follows:
        Here are the Wikipedia pages that support the answer:
        From question:
        1. Page Title : URL
        2. Page Title : URL
        ...
        Inferred keywords:
        1. Page Title : URL
        2. Page Title : URL
        ...
        """)
## Summarize Wiki page  
    system_message_content = (""""Below is a Wiki page file segmented by text-tiling. To help you structure a comprehensive summary, please follow these steps:
    1. Identify the different perspectives presented in each segment.
    2. Outline the main themes discussed throughout the text.
    3. Compare and contrast the viewpoints in each segment, highlighting any notable contradictions or agreements.
    4. Conclude by synthesizing any consensus found within the content."""  
## Summarize Speech
    message_content = """The following text is a transcription of a speech originally delivered in audio format. 
    It contains specialist terminology specific to the speaker's region. 
    Please provide a concise summary that lists the main points and the speaker's views.""")

## Generated Answer
### Prompt Chaining  

    system_message_content = ("""To effectively address audience questions, let's break down the process into four main components:
    1. Questions from the Audience: Start by considering the specific questions raised by the audience. What are they asking? Identifying the exact questions will guide the response process.
    2. Speech: Next, reflect on the speech content that the audience has just listened to. It's crucial to connect the questions to the content of the speech since it may contain pertinent information that could help answer these questions.
    3. Keywords: Then, extract key terms from both the questions and the speech. These keywords act as a bridge, linking the audience's inquiries with the relevant sections of the speech. They are instrumental in honing in on the parts of the speech that are most relevant to the questions asked.
    4. Wikipedia References: Finally, to provide thorough and well-supported answers, consult relevant Wikipedia pages. These references can offer deeper or more detailed information that supports the answers derived from the speech and identified keywords.)
    """

    
    system_message_content = ("""Armed with a summary of the speech, the specific questions from the audience, key terms, and Wikipedia references, assume the role of the speaker to answer the questions. 
    Your goal is to provide informative and helpful answers that directly address the audience's questions while staying connected to your original speech content.""")

### Speech Only  
    system_message_content = ("""Imagine you're a speaker who has just delivered a speech at a conference, and the audience is asking you questions. In your responses, please consider the following:
    Understand the Audience's Questions: Listen carefully to what is being asked to ensure you address their specific concerns.
    Refer to Your Speech Content: Connect your answers to the key points from your speech to maintain relevance.
    """)
## LLM rating prompt
    prompt_request = """
    Objective: Evaluate the alignment between an original answer and a generated answer based on criteria such as consistency, style, and accuracy.

    Step-by-Step Guide:
    Read Each Pair of Answers: You will be provided with both an original answer and a generated answer corresponding to a specific question.
    Rate Each Pair: Assess and rate each pair based on the criteria provided below using a scale from 1 to 5:
    Consistency: Does the generated answer maintain the same information and tone as the original answer?
    Style: Does the generated answer's style (formality, clarity, engagement) align with that of the original?
    Accuracy: Is the information in the generated answer accurate and well-supported by reliable sources?
    Provide Feedback: For each criterion, include a brief comment explaining your rating. This feedback will help identify the strengths and weaknesses of the generated answers.
    Rating Scale:
    1: Very Poor – Significant improvements needed.
    2: Poor – Needs multiple refinements.
    3: Average – Sufficient but with noticeable flaws.
    4: Good – Well-executed with minor issues.
    5: Excellent – Meets or exceeds expectations flawlessly.
    Evaluation Format:
    For each pair of answers, provide your ratings as follows:

    Consistency: score
    Style: score
    Accuracy: score
    """
