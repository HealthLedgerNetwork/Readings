# 1. Revolutionizing Medical Data Sharing Using Advanced Privacy Enhancing Technologies: Technical, Legal and Ethical Synthesis

# PDF:
Scheibner, J., Raisaro, J. L., Troncoso-Pastoriza, J. R., Ienca, M., Fellay, J., Vayena, E., & Hubaux, J. P. (2021). Revolutionizing Medical Data Sharing Using Advanced Privacy-Enhancing Technologies: Technical, Legal, and Ethical Synthesis. *Journal of medical Internet research*, *23*(2), e25120. https://doi.org/10.2196/25120

# Authors

| Name | Institutions’ numbers | Institution(s) |
| --- | --- | --- |
| James Scheibner | 1 | (1) - Health Ethics and Policy Laboratory, Department of Health Sciences and Technology, ETH Zürich, Zürich, Switzerland |
| Jean Louis Raisaro | 2,3 | (2) -Precision Medicine Unit, Lausanne University Hospital, Lausanne, Switzerland |
| Juan Ramón Troncoso-Pastoriza | 4 | (3) - Data Science Group, Lausanne University Hospital, Lausanne, Switzerland |
| Marcello Ienca | 1 | (4) - Laboratory for Data Security, School of Computer and Communication Sciences, EPFL, Lausanne, Switzerland |
| Jacques Fellay | 2,5,6 | (5) - School of Life Sciences, EPFL, Lausanne, Switzerland |
| Effy Vayena | 1 | (6) - Host-Pathogen Genomics Laboratory, Swiss Institute of Bioinformatics, Lausanne, Switzerland |
| Jean-Pierre Hubaux | 4 |  |

---

# Summary

# 1. Abstract

This paper provides a synthesis between ***two novel advanced privacy-enhancing
technologies*** (PETs): **Homomorphic Encryption** and **Secure Multiparty Computation** (together *Multiparty Homomorphic Encryption* **MHE**)

**MHE** ***fulfills legal requirements for medical data sharing under the General Data Protection Regulation*** (**GDPR**) which has set a global benchmark for data protection

**The challenge** is to ***conduct data sharing that preserves individual privacy and data usability**.*

# 2. Introduction

The current biomedical research paradigm has been characterized by a **shift** *from intra-institutional research* towards *multiple collaborating institutions* operating at an inter-institutional, national or international level for multisite research projects.

*Differences* between *ethical and legal* requirements at all *jurisdictional levels*

There are numerous organizational strategies that have been used
to resolve these issues, particularly for international academic consortia.

The International Cancer Genome Consortium (ICGC) endeavors to amass cancer
genomes paired with non-cancerous sequences in a cloud environment, known as the Pan
Cancer Analysis of Whole Genomes

<aside>
💡 **Within EU** there is the **potential for differences** in ***how countries regulate the processing of health related personal data***

</aside>

Present the **best** available **solutions** *remain contractual and technological measures*.

In this paper, we describe how *traditional data-sharing approaches relying on conventional
privacy-enhancing technologies* (PETs) *are limited by various regulations governing medical use and data sharing.*

# 3. Privacy and security issues of current medical data-sharing models

**Examine** the ***main models for exchanging medical data*** for research purposes ***and the limitations of conventional privacy protection mechanisms*** ***that are currently used*** ***to reduce the risk of re-identification***.

We synthesize the data-sharing models into ***three categories*** and ***analyze their main technological issues:***

## 1. ***Centralized model: trusted dealer***
The centralized model requires medical sites (i.e., data providers) that are willing to share data with each other to pool their individual-level patient data into a single repository.

The data repository is usually hosted by one medical site or by an external third party playing the trusted dealer role.

Main advantage of this model is that the trusted dealer enables authorized investigators to access all the patient-level information needed for data cleaning and for conducting statistical analysis.

Such a data-sharing model minimizes infrastructure costs at medical sites as data storage and computation are outsourced.

From a data privacy perspective the centralized model is often difficult to realize, especially when medical and genetic data have to be exchanged across different jurisdictions.

The central site hosting the data repository represents a single point of failure in the data-sharing process.  All participating sites have to trust such a single entity for protecting their patient-level data

To minimize sensitive information leakage from data breaches, traditional anonymization
techniques include suppressing of directly identifying attributes, as well as the generalizing,
aggregating or randomizing quasi-identifying attributes in individual patient records.

<aside>
💡 **k-anonymity privacy-model** - is a well-established privacy-preserving model that *reduces* the likelihood of *re-identification attacks* “signaling out” an individual. It *ensures* that for each *combination of quasi (or indirect) identifiers there exists at least k individuals who share the same attributes.*

</aside>

Sophistication of re-identification attacks and the rising dimensionality of patient data, the above-mentioned countermeasures are inadequate to ensure a proper level of anonymization and preserve acceptable data utility. Therefore, these conventional anonymization techniques are rarely used in practice. Researchers prefer to rely on simple pseudonymization techniques ( such as replacing direct identifiers with pseudonymous codes) combined with legal measures defining each party’s responsibilities regarding data transfer, access and use. *This process generates administrative overheads that slow down the pace of biomedical research.*

Contractual safeguards may not eliminate the risk of individuals being reidentified. Combining traditional pseudonymization mechanisms and governance strategies meet the legal standard of pseudonymization but not anonymization under the GDPR.

## 2. ***Decentralized model: site-level meta-analysis***

For each clinical study, the statistical analysis is first computed on local datasets.

The resulting local statistics are then sent to the site responsible for the final meta-analysis that aggregates the separate contribution of each data provider to obtain the final result of the analysis. 

The site performing the meta-analysis is trusted by all other sites for the protection of their local statistics. 

Local statistics have a significantly lower dimensionality with respect to individual-level data, there is a lower risk of re-identification in the decentralized model.

Some aggregate-level statistics may be too low for certain subpopulations ( such as patients with rare diseases) can be considered personally identifying. In some circumstances, aggregate-level data from local analyses can be exploited to detect the presence of target individuals in the original dataset.

This membership information can be subsequently used to infer sensitive and sometimes attributes of the target individual. For example, detecting the membership of an individual in a HIV-positive cohort reveals her HIV status. The intuition behind these attacks is to measure the similarity between the individual-level target data with statistics computed from the study datasets and statistics computed from the general population. The attacker’s certainty about the target’s membership in the dataset increases with the similarity of the target’s data to the statistics derived from the study dataset.

To address these inference attacks, clinical sites can anonymize their local statistics by applying obfuscation techniques that mainly consist in adding a certain amount of statistical noise on the aggregate-level data before transfer to third parties. This process enables data providers to achieve formal notions of privacy such as ***differential privacy***.

<aside>
💡 **Note:** *Differential privacy* is a privacy-preserving concept that aims to protect the privacy of individuals in statistical analysis. It ensures that the inclusion or exclusion of an individual's data in a dataset does not significantly impact the results or reveal sensitive information about that individual. By adding statistical noise or perturbation to the data, differential privacy provides a mathematical guarantee of privacy while still allowing useful analysis to be performed. It is commonly used in decentralized models of data sharing to mitigate the risk of re-identification and protect individuals' privacy.

</aside>

In the statistical privacy community, differential privacy is currently considered as guaranteeing the likelihood of reidentification from the release of aggregate-level statistics can be minimized to a quantifiable value.

Similar to anonymization techniques for individual-level data, statistical obfuscation techniques degrade the utility of aggregate-level data. Consequently, the amount of noise introduced by data obfuscation has to be carefully calibrated to reach the desired compromise between utility and privacy. Often, when each data provider adds the required amount of noise to reach an acceptable level of privacy, the resulting aggregated results stemming from a meta-analysis are too distorted to be reliable

Beyond privacy considerations, this approach also suffers from a lack of flexibility as the medical sites involved in the analysis have to coordinate before the analysis on the choice of parameters and covariates to be considered. This coordination often depends on manual approval, impeding the pace of the analysis itself. Finally, as opposed to the centralized approach, accuracy of results from a meta-analysis that combines the summary statistics or results of local analysis can be affected by cross-study heterogeneity. This can lead to inaccurate and misleading conclusions

## 3. ***Decentralized model: federated analysis and learning***
The federated model is an evolution of the decentralized model based on site-level meta-analysis.
Instead of sharing the results of local analyses, the participating data providers collaborate to
perform a joint analysis or the training of a machine learning model in an interactive and iterative
manner, only sharing updates of the model’s parameters.

One of the medical sites participating in the multi-centric research project (typically the site responsible for the statistical analysis) becomes the reference site (or central site) and defines the model/analysis to be trained and executed on the data distributed across the network.

This model is referred to as the “global” model. Each participating site is given a copy of the model to train on their own individual-level data. Once the model has been trained locally for a number of iterations, the sites send only their updated version of the model parameters (aggregate-level information) to the central site and keep their individual-level data at their premises. The central site aggregates the contributions from all the sites and updates the global model. Finally, the updated parameters of the global model are shared again with the other sites. The process repeats iteratively till convergence of the global model.

With respect to the distributed data-sharing approach based on site-level meta-analysis, this federated approach is more robust against heterogeneous distributions of the data across different sites, thus yielding results accuracy that is comparable to the results obtained with the same analysis conducted using the centralized model. Moreover, this approach does not suffer from the loss in statistical power of conventional meta-analyses. Prominent projects that have attempted to employ federated approaches to analysis and sharing of biomedical data are the ***DataSHIELD*** project and the ***Medical Informatics Platform of the Human Brain Project***.

### What does federated mean and what is federated learning:

**Federated** refers to a decentralized approach or model where multiple entities or organizations collaborate and share resources, data, or knowledge while retaining control and ownership over their individual components. It involves coordination and cooperation among the participating entities without the need for a central authority or data repository.

**Federated learning** is a specific application of the federated model in the context of machine learning. It is a privacy-preserving approach where machine learning models are trained collaboratively on distributed data without the need to share the raw data itself. In federated learning, each participating entity trains the model locally on its own data and only shares the model updates or parameters with a central server or coordinator. The central server aggregates these updates from multiple entities and iteratively improves the global model without accessing or exposing the underlying data.

Federated learning enables privacy protection and data security by keeping the data decentralized and minimizing the risk of data leakage or re-identification. It allows organizations to leverage the collective knowledge and insights from diverse datasets while respecting data privacy and confidentiality.

The federated data-sharing approach combines the best features of the other two approaches.
However, although the risk or re-identification is reduced compared to the centralized approach,
the federated approach remains vulnerable to the same inference attacks of the meta-analysis
approach. These inference attacks exploit aggregate-level data released during collaboration.

The potential for an inference attack is even increased compared to a meta-analysis-based approach. This is due to the iterative and collaborative nature of the data processing, allowing adversaries to observe model changes over time and with specific model updates. Melis et al show that updates of model parameters transferred during the collaborative training phase can be used to infer the membership of a target individual in the training datasets as well as some properties associated with a particular subset of the training data. This inference is possible if the context of the data release enables the attacker to easily access some auxiliary individual-level information about the target individual. In legal terms (as discussed below), these aggregate-level data can potentially be considered personal data. As for the meta-analysis approach, the use of obfuscation techniques can be used to anonymize model’s updates at each iteration. Nevertheless, the required perturbation can severely affect the performance of the final model.

## ***Conclusion***

Finally, regardless of the type of distributed data-sharing model, obfuscation techniques for anonymizing aggregate-level data are rarely used in practice in medical research because of their impact on data utility. As a result, these technical privacy limitations are usually addressed via additional legal and organizational mechanisms. For the DataSHIELD project, access is limited to organizations that have consented to the terms of use for DataSHIELD and have sought appropriate ethics approval to participate in a DataSHIELD analysis. Therefore, implementing the platform will require cooperating with governments and institutions so they are comfortable with exposing sensitive data to the platform [27]. However, as we discuss below, advanced PETs can also guarantee data privacy.

# 4. Minimizing risks by leveraging advanced PETs

A number of cryptographic PETs have emerged as significant potential advances for addressing the above-mentioned data protection challenges that still affect medical data sharing in the decentralized model

Although hardware-based approaches could be envisioned for this purpose, they are usually tailored to centralized scenarios and introduce a different trust model involving the hardware provider. Further, they also depend on the validity of the assumptions on the security of the hardware platform, for which new vulnerabilities are constantly being discovered.

In this paper, we focus on two of the most powerful software-based PETs Homomorphic Encryption and Secure Multiparty Computation. Both rely on mathematically proven guarantees for data confidentiality, respectively grounded on cryptographic hard problems and non-collusion assumptions.

## 1. **Homomorphic Encryption**

- a special type of encryption that supports computation on encrypted data (ciphertexts) without decryption
- homomorphically encrypted data can be securely handed out to third parties, who can perform meaningful operations on them without learning anything about their content
- fully homomorphic encryption schemes, or schemes enabling arbitrary computations on ciphertexts, are still considered nonviable due to the high computational and storage overheads they introduce.
- current practical schemes that enable only a limited number of computations on ciphertexts (such as polynomial operations) have reached a level of maturity that permits their use in real scenarios.

## 2. **Secure Multiparty Computation**

- ***Protocol*** that ***enables multiple parties to jointly compute functions over their private inputs without disclosing*** to the ***other parties more information about their inputs*** ***than what can be inferred from the output of the computation***.
- This class of protocols is particularly attractive in privacy-preserving distributed analytic platforms due to the great variety of secure computations they enable
- However, this flexibility includes a number of drawbacks that hinder their adoption, including high network overhead and parties required to be online during computation.

## More On SMC


## 3. **Multiparty Homomorphic Encryption**

- The combination of SMC and HE was proposed to overcome their respective overheads and technical limitations; we refer to it as Multiparty Homomorphic Encryption (MHE)
- Enables flexible secure processing by efficiently transitioning between encrypted local computation, performed with HE, and interactive protocols SMC.
- Can be used to choose the most efficient approach for each step within a given workflow, leveraging the properties of one technique to avoid the bottlenecks of the other
- Ensures that the secret key of the underlying HE scheme never exists in full. Instead, it distributes the control over the decryption process across all participating sites, each one holding a fragment of the key. All participating sites have to agree to enable the decryption of any piece of data, and no single entity alone can decrypt the data.
- Unlike HE or SMC alone, MHE provides effective, scalable and practical solutions for addressing the privacy-preserving issues that affect the distributed/federated approach for data sharing.
- For example, systems such as Helen, MedCo, or POSEIDON use MHE to guarantee that all the information interchanged between the sites is always in encrypted form, including aggregate data such as model parameters and model updates, and only the final result (the computed model or the predictions based on this model) is revealed to the authorized user.
- MHE reduces the need of obfuscation techniques to protect aggregate-level data from inference attacks. Further, data utility, which is typically lost with privacy-preserving distributed approaches that only rely on obfuscation techniques, can be significantly improved.
- As aggregate-level data transfer and processing across participating sites during the analysis or training phase remains always encrypted, obfuscation can be applied only to the decrypted final result of the analysis that is released to the data analyst, instead of being applied to all local model updates at each iteration.
- Hence, MHE enables a much lower utility degradation for the same level of reidentification risk.

## More on Multiparty Homomorphic Encryption

[***Multiparty Homomorphic Encryption - Theory + Systems that use it*** ]

# 5. Regulatory hurdles for the use of encryption technologies

# 6. Advanced PETs and EU data governance requirements

# 7. Regulatory instruments to encourage the use of novel PETs

# 8. Conclusion

---

# Scheme:
