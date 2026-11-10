## structure du projet

```
Bug-Brother/
├── mcp_tools_mbpp.py        # serveur mcp pour mbpp, donne run_tests à l'agent
├── mcp_tools_swebench.py    # serveur mcp pour swe-bench, tous les outils obligatoires
├── sandbox_template.json    # config par défaut du sandbox, c'est ici qu'on règle
├── BENCHMARK_REPORT.md      # les modèles testés et ceux qu'on a gardés
├── src/
│   ├── bug_brother/         # le cœur, les deux agents tournent dessus
│   │   ├── models.py        # modèles pydantic partagés, on n'y touche pas seul
│   │   ├── llm/             # parle aux providers, fait tourner les clés, retente
│   │   ├── agent/           # la boucle : réfléchir, écrire du code, le lancer, regarder, recommencer
│   │   ├── sandbox/         # fait tourner le code du llm enfermé + le repl
│   │   └── tools/           # ce que font vraiment les outils mcp
│   ├── agent_mbpp/          # python -m agent_mbpp
│   └── agent_swebench/      # python -m agent_swebench
├── tests/                   # nos tests, dont les attaques sur le sandbox
├── configs/                 # modèles et providers
└── solutions/               # les solution.json derrière le benchmark
```

en gros : tout ce qui réfléchit est dans llm/ et agent/, tout ce qui exécute est dans sandbox/ et tools/
