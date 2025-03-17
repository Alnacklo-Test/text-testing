# text-testing

1) Crear organizacion
2) Crear 2 o mas repositorios
3) Crear PAT fine-grained
4) Habilitar PAT en nuestra organizacion (con permisos de owner)
5) Secrets en el repositorio
6) Crear carpetas .github/workflows
7) Crear instrucciones .yml para las consultas a la API

//new list

1)Habilitar Github Actions en el repositorio
2) Crear un Github Project v2 dentro de la organizacion
3) Obtener id de los proyectos de la organizacion

    //obtener proyectos
    alnacklo@alnacklo-ThinkBook-16-G6-ABP:~  $ curl -X POST -H "Authorization: Bearer github_pat_xxx" \
        -H "Accept: application/vnd.github.v3+json" \
        https://api.github.com/graphql \
        -d '{ "query": "query { organization(login: \"ORG_NAME\") { projectsV2(first: 10) { nodes { id title } } } }" }'

4) Identificar el proyecto deseado
5) Obtener los ID de los estados del proyecto 

    //Obtener los fields del proyecto (status, priority, size)
    curl -X POST -H "Authorization: Bearer github_pat_xxx" \
        -H "Accept: application/vnd.github.v3+json" \
        https://api.github.com/graphql \
        -d '{ "query": "query { node(id: \"PVT_kwDODB6w4M4A0YLS\") { ... on ProjectV2 { fields(first: 20) { nodes { ... on ProjectV2SingleSelectField { id name } } } } } }" }'

6) Obtener los ID de los valores "Status" (Backlog, ToDo, In Progress, Dev)

    //obtener status del project
    curl -X POST -H "Authorization: Bearer github_pat_xxx" \
        -H "Accept: application/vnd.github.v3+json" \
        https://api.github.com/graphql \
        -d '{ "query": "query { node(id: \"PVTSSF_lADODB6w4M4A0YLSzgqBSYE\") { ... on ProjectV2SingleSelectField { options { id name } } } }" }'

7)