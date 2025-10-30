FORMAT DE CAS D’UTILISATION.

NOM DU CAS

BRÈVE DESCRIPTION
The role and purpose of the use case.  A single paragraph should suffice for this description.

FLUX D’ÉVÉNEMENTS
Flux de Base

This use case starts when the actor does something. An actor always initiates use cases. The use case should describe what the actor does and what the system does in response. The use case should be phrased in the form of a dialogue between the actor and the system.

The use case should describe what happens inside the system but not how or why. If information is exchanged, be specific about what is passed back and forth. For example, it is not very illuminating to say that the actor enters customer information; it is better to say that the actor enters the customer’s name and address. A glossary is often useful to keep the complexity of the use case manageable; you may want to define customer information there, to keep the use case from drowning in details.

Simple alternatives may be presented within the text of the use case. If it takes only a few sentences to describe what happens when there is an alternative, do it directly within the flow-of-events section. If the alternative flows are more complex, use a separate section. For example, an alternative flow describes how to describe more complex alternatives.


Flux Alternatifs

1.	Premier Flux Alternatif: More complex alternatives should be described in a separate section, which is referred to in the basic flow-of-events section. Think of the alternative flow sections as alternative behavior; each alternative flow represents alternative behavior (many times, because of exceptions that occur in the main flow). They may be as long as necessary to describe the events associated with the alternative behavior. When an alternative flow ends, the events of the main flow of events are resumed unless otherwise stated.

Alternative flows may, in turn, be broken down into subsections.

2.	Second Flux Alternatif:  There may be, and most likely will be, a number of alternative flows in a use case. Keep each alternative separate, to improve clarity. Using alternative flows improves the readability of the use case, as well as presents use cases from being decomposed into hierarchies of use cases. Keep in mind that use cases are just textual descriptions and that their main purpose is to document the behavior of a system in a clear, concise, and understandable way.
Exigences Spéciales
These are typically nonfunctional requirements that are specific to a use case but are not easily or naturally specified in the text of the use case’s event flow. Examples of special requirements include legal and regulatory requirements, application standards, and quality attributes of the system to be built, including usability, reliability, performance, or supportability requirements. Other requirements, such as operating systems and environments, compatibility requirements, and design constraints, should also be captured in this section.
1.	First special requirement.

Pré-conditions
Precondition of a use case is the state of the system that must be present prior to a use case being performed.
1.	Precondition 1.

Post-conditions
Postcondition of a use case is a list of possible states the system can be in immediately after a use case has finished.
1.	Postcondition 1.

EXAMPLES D’UTILISATION SELON LE USE CASE DIAGRAM.

Description of Use Cases -Example
▪
Name: Reserve lecture hall
▪
Short description: An employee reserves a lecture hall at the university for an event.
▪
Precondition: The employee is authorized to reserve lecture halls.
▪
Postcondition: A lecture hall is reserved.
▪
Error situations: There is no free lecture hall.
▪
System state in the event of an error: The employee has not reserved a lecture hall.
▪
Actors: Employee
▪
Trigger: Employee requires a lecture hall.
▪
Standard process: 
(1) Employee logs in to the system.
(2) Employee selects the lecture hall.
(3) Employee selects the date.
(4) System confirms that the lecture hall is free.
(5) Employee confirms the reservation.
▪
Alternative processes: 
(4’) Lecture hall is not free.
(5’) System proposes an alternative lecture hall.
(6’) Employee selects alternative lecture hall and confirms the reservation.
