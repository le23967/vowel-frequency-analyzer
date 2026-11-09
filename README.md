# Vowel Frequency Analyzer

A custom GitHub Action built with Docker. Every push to `main` builds the Docker image and runs it. The container counts the vowels (a, e, i, o, u) in `data.txt` and appends the counts to this README, together with the contributor's GitHub username and a timestamp.

## Why

Contributors often upload raw text files to this repository. Running the analysis on every push keeps the results up to date without anyone running a script by hand, and the README keeps a record of who changed the data and when. The project is also a hands-on exercise in the parts of a Docker-based custom action: a Dockerfile, an ENTRYPOINT script that runs other scripts, and a workflow that passes the contributor's username into the container.

## Project structure

```
vowel-frequency-analyzer/
├── README.md                         # Targeted for update using update_readme.sh
├── Dockerfile                        # Dockerfile at the root
├── .github/
│   ├── actions/
│   │   └── vowel-frequency-analyzer/
│   │       └── action.yml            # Action definition
│   ├── workflows/
│   │   └── ci.yml                    # Workflow definition
│   └── scripts/
│       ├── frequency.py              # Frequency script
│       ├── update_readme.sh          # Script to update README
│       └── entrypoint.sh             # Entrypoint shell script
└── data.txt                          # Required input data
```

## Vowel frequency results

Each push to `main` adds a line below: `[username - vowel counts - timestamp]`.

[le23967 - Counter({'e': 27, 'i': 20, 'o': 18, 'a': 15, 'u': 11}) - Tue Oct 20 07:13:29 UTC 2026]

[le23967 - Counter({'e': 34, 'o': 26, 'i': 24, 'a': 20, 'u': 14}) - Mon Nov  9 18:44:20 UTC 2026]
