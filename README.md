
# Project Title 
Building AI course project - Building ISRTS for incoming IT service requests

## Summary

ISRTS is an AI‑powered tool that automatically categorizes, prioritizes, and routes incoming IT service requests. Instead of relying on manual triage—which is slow, inconsistent, and resource‑intensive—the system uses natural language processing (NLP) to interpret request descriptions and assign them to the correct support queue with an appropriate priority level.


Background
The problem
Most IT organizations struggle with:
•	High volumes of service tickets
•	Inconsistent triage due to human interpretation
•	Delays in routing requests to the right teams
•	Rework caused by misclassification
This problem is extremely common in mid to large enterprises, especially those with multiple support teams (network, SAP, M365, security, hardware, etc.).
Personal motivation
As a project manager who has led large digital transformation programs, you’ve seen firsthand how much time is wasted in manual triage. Automating this step improves service quality, reduces SLA breaches, and frees analysts to focus on higher value work.
Why it matters
•	Faster response times improve employee satisfaction
•	Reduced operational cost
•	Better data quality for reporting and forecasting
•	A scalable foundation for future automation (chatbots, self service, predictive analytics)
________________________________________
Data and AI techniques
Data sources
•	Historical service tickets (titles, descriptions, categories, priorities, resolution codes)
•	User metadata (department, location, device type)
•	System logs (optional, for advanced correlation)
Data requirements
•	At least 5,000–10,000 historical tickets for a reliable model
•	Clean, consistently labeled categories
•	Removal of sensitive information (PII)
AI techniques
•	Natural Language Processing (NLP) for text classification
•	Supervised machine learning (e.g., logistic regression, random forest, or a small transformer model)
•	Confidence scoring to determine when human review is needed
•	Optional: clustering to discover new ticket categories
Optional demo idea
Use a small dataset of sample tickets and train a simple classifier:
from sklearn.feature_extraction.text import TfidfVectorizer
from sklearn.linear_model import LogisticRegression

tickets = ["Laptop won't start", "Password reset needed", "VPN not connecting"]
labels = ["Hardware", "Access", "Network"]

vectorizer = TfidfVectorizer()
X = vectorizer.fit_transform(tickets)

model = LogisticRegression()
model.fit(X, labels)

print(model.predict(vectorizer.transform(["Cannot connect to WiFi"])))
This demonstrates the core concept in a lightweight way.
________________________________________
How it is used
Primary users
•	IT service desk analysts
•	Support teams (network, SAP, security, etc.)
•	End users submitting tickets (indirectly)
Workflow
1.	User submits a ticket through the service portal.
2.	ISRTS analyzes the text in real time.
3.	The system assigns: 
o	Category
o	Priority
o	Recommended resolver group
4.	Analysts review or approve the suggestion.
5.	Ticket is routed automatically.
Stakeholder viewpoints
•	Analysts: reduced manual workload
•	Support teams: fewer misrouted tickets
•	End users: faster resolution
•	Leadership: improved SLA performance and reporting accuracy
________________________________________
Challenges
•	AI may misclassify rare or ambiguous tickets
•	Requires clean historical data
•	Human oversight is still needed for low confidence predictions
•	Doesn’t solve underlying IT issues—only improves routing
•	Change management is essential (analysts must trust the model)
________________________________________
What’s next
Future enhancements could include:
•	A conversational chatbot that resolves simple issues automatically
•	Predictive analytics to forecast ticket volumes
•	Integration with device telemetry for proactive incident detection
•	Automated root cause suggestions
•	Multi language support for global teams
________________________________________
Acknowledgments
This project draws on:
•	Open source NLP libraries such as scikit learn, spaCy, and Hugging Face Transformers
•	ITIL service management best practices
•	Inspiration from real world service desk automation tools and academic research on text classification
