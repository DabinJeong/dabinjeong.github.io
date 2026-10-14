---
# Leave the homepage title empty to use the site title
title: ''
summary: ''
date: 2022-10-24
type: landing

sections:
  - block: resume-biography-3
    id: about
    content:
      username: me
      text: ''
      headings:
        about: 'About me'
        education: 'Education'
        interests: 'Research Interests'
    design:
      name:
        size: md
      avatar:
        size: medium
        shape: circle

  - block: markdown
    id: research
    content:
      title: 'Research'
      text: |-
        I see DNA as both a code and a codebook, deeply intertwined. My long-term goal is to build a program that simulates biological systems starting from DNA sequence.

        > *What I cannot create, I do not understand.* — Richard Feynman

        Right now I work on multi-modal learning that connects histopathology images with spatial transcriptomics, generative models for regulatory DNA, and modeling how cells change over time.
    design:
      columns: '1'

  - block: markdown
    id: experience
    content:
      title: 'Experience'
      text: |-
        - **Senior Data Scientist**, [Wellcome Sanger Institute](https://www.sanger.ac.uk/group/lotfollahi-group/) (2024.10–) — Lotfollahi Lab
        - **Research Intern**, LG AI Research (2024.01–2024.04)
        - **Ph.D.**, Bioinformatics, [Seoul National University](https://www.snu.ac.kr) (–2024.08)
        - **B.S.**, Biochemistry, [Yonsei University](https://www.yonsei.ac.kr) (–2018.08)
    design:
      columns: '1'

  - block: collection
    id: publications
    content:
      title: 'Publications'
      text: 'Full list on [Google Scholar](https://scholar.google.com/citations?hl=en&user=Ne2p354AAAAJ).'
      filters:
        folders:
          - publications
    design:
      view: citation

  - block: markdown
    id: talks
    content:
      title: 'Talks & Awards'
      text: |-
        - **2026** · Selected participant (500 of 6,000+ applicants), Claude Life Sciences Hackathon, Anthropic × Gladstone Institutes — built a generative model to infer missing cell states across time points
        - **2023** · Invited talk, National Heart & Lung Institute, Imperial College London — *Deep graph attention for multi-omics network biomarkers in eosinophilic asthma* (host: Prof. Kian Fan Chung)
        - **2016** · National Excellence Scholarship (Natural Sciences and Engineering) — sole recipient in the department
    design:
      columns: '1'

  - block: markdown
    id: beyond
    content:
      title: 'Beyond Research'
      text: |-
        - **Tools** · Python, R, PyTorch, PyTorch Geometric, DGL, Nextflow, Snakemake, Docker
        - **Languages** · Korean (native), English (professional), Spanish (conversational)
        - **Off the clock** · Knitting, board games and chess, and linguistics — especially how symbols relate to concepts
        - **Favorite books** · *Gödel, Escher, Bach*; *Surfaces and Essences*; *Language as a Cognitive Process*
    design:
      columns: '1'
---
