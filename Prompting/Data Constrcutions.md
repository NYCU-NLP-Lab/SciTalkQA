## Find Keyword  
    prompt_request =  (
        "Please list the Wikipedia pages that support the answer to the given question "
        "and its corresponding answer. Divide the pages based on where the keywords come from: "
        "if the keyword is from the question, list it under 'From question'; "
        "if it is only present in the answer and not in the question, list it under 'From answer'. "
        "Format your response as follows:\n"
        "Here are the Wikipedia pages that support the answer:\n"
        "From question:\n"
        "1. Page Title + URL\n"
        "2. Page Title + URL\n"
        "...\n"
        "From answer:\n"
        "1. Page Title + URL\n"
        "2. Page Title + URL\n"
        "..."
    )

