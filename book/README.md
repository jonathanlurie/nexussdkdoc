# BlueBrain Nexus
The BlueBrain Nexus is a provenance based, semantic enabled data management platform enabling the definition of an arbitrary domain of application for which there is a need to create and manage entities as well as their relations (e.g. provenance). For example, the domain of application managed by the Nexus platform deployed at Blue Brain is to digitally reconstruct and simulate the brain.

At the heart of the BlueBrain Nexus platform lies the Knowledge Graph; at BlueBrain, it will allow scientists to:

1. Register and manage neuroscience relevant entity types through schemas that can reuse or extend community defined schemas (e.g. schema.org, bioschema.org, W3C-PROV) and ontologies (e.g. brain parcellation schemes, cell types, taxonomy).

2. Submit data to the platform and describe their provenance using the W3C PROV model. Provenance is about how data or things are generated (e.g. protocols, methods used…), when (e.g. timeline) and by whom (e.g. people, software…). Provenance supports the data reliability and quality assessment as well as enables workflow reproducibility. Platform users can submit data either through web forms or programmatic interfaces.

3. Search, discover, reuse and derive high-quality neuroscience data generated within and outside the platform for the purpose of driving their own scientific endeavours. Data can be examined by species, contributing laboratory, methodology, brain region, and data type, thereby allowing functionality not currently available elsewhere. The data are predominantly organised into atlases (e.g. Allen CCF, Waxholm) and linked to the KnowledgeSpace – a collaborative community-based encyclopedia linking brain research concepts to the latest data, models and literature.

It is to be noted that many other scientific fields (Astronomy, Agriculture, Bioinformatics, Pharmaceutical Industry, …) are in need of such a technology. Consequently, BlueBrain Nexus core technology is being developed to be agnostic of the domain it might be applied to.

The Nexus platform is made up of a collection of services and web applications that work together to manage data stored within the system. The services and web applications are powered by a collection of libraries and tools built specifically to address the needs of the platform. Underneath it all there are popular open source technologies that we all know and love.

# Nexus SDK and CLI
The Nexus SDKs are available in Python and Javascript and is made mainly for developers and data scientists. The command line interpreter (CLI) provides an easy access to Nexus for non-programmers.

Both the SDKs and CLI are mimicking the capabilities of the Nexus [REST API](https://bluebrain.github.io/nexus/docs/api/index.html) but add a nice top layer to make things easier.
