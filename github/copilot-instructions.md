TABLE DES MATIÈRES
Normally, a use case specification will not be long enough to warrant a table of contents for the use case. But this element may be required if the use case presents unusual problems in finding portions of the specification.

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

Points d’Extension 
Extension points of the use case.
1.	Name of extension point.

Definition of the location of the extension point in the flow of events.
Other Use Case Material.

Contraintes
1.	Chaque cas d'utilisation doit être associé à une caractéristique.
2.	Les cas d'utilisation doivent être numérotés de manière unique (par exemple, RVSQ-UC-01).
3.	Les cas d'utilisation doivent être rédigés en français clair et compréhensible.
4.	Les cas d'utilisation peuvent inclure des flux alternatifs pour gérer les scénarios exceptionnels.
