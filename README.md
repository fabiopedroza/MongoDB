# MongoDB - Dia 01/Nov
Manipulação da collection - Turma 01 Gama PAN
![image](https://user-images.githubusercontent.com/92064386/138007156-3ae6e393-a770-4bf7-85cb-9f9d390fb118.png)
![image](https://user-images.githubusercontent.com/92064386/138007193-47cac947-928e-4909-a299-0ae99b35eed9.png)


##
Atividades:

# Inserção dos dados

# --> Inserção 01
##
{
    "professor": {
        "nome": "Ana",
        "cpf": "17282829187",
        "disciplina": "robotica",
        "telefone": "(11) 3287-12112"
    },
    "aluno": {
        "nome": "Fabio Pedroza",
        "telefone": "(61) 98288-8877"
    },
    "disciplina": "Java",
    "nota final": "7.0",
    "aprovacao": "aprovado",
    "dataHora": {
        "$date": "2021-07-12T10:00:20.000Z"
    }
}

# --> Inserção 02
##
{
    "professor": {
        "nome": "Jenifer",
        "cpf": "012.456.987-00",
        "disciplina": "mongo",
        "telefone": "(21) 4444-1212"
    },
    "aluno": {
        "nome": "Mateus Almeida",
        "telefone": "(85) 98288-8877"
    },
    "disciplina": "Python",
    "nota final": "10.0",
    "aprovacao": "aprovado",
    "dataHora": {
        "$date": "2021-07-12T11:00:20.000Z"
    }
}

# --> Inserção 03
##
{
    "professor": {
        "nome": "Jonathan",
        "cpf": "098.456.123-00",
        "disciplina": "java",
        "telefone": "(21) 4444-1212"
    },
    "aluno": {
        "nome": "fernanda",
        "telefone": "(44) 98288-8877"
    },
    "disciplina": "nodes",
    "nota final": "5.0",
    "aprovacao": "recuperaao",
    "dataHora": {
        "$date": "2021-07-12T12:00:20.000Z"
    }
}

# --> Inserção 04
##
{
    "professor": {
        "nome": "cleber",
        "cpf": "998.456.123-00",
        "disciplina": "java",
        "telefone": "(21) 4444-1212"
    },
    "aluno": {
        "nome": "fernanda Ayres",
        "telefone": "(18) 98288-8877"
    },
    "disciplina": "nodes",
    "nota final": "9.0",
    "aprovacao": "aprovado",
    "dataHora": {
        "$date": "2021-07-12T12:00:20.000Z"
    }
}

# --> Consulta todos os documentos
## 
db.getCollection('JAVA').find()

# --> Consulta por field específica 
##
db.getCollection('JAVA').find({"aluno.nome":"fernanda" })

# --> Update na field (nome.aluno)
##
db.getCollection('JAVA').update(
    // query 
    {
        "aluno.nome":"fernanda"
    },
    
    // update 
    { $set:
        { "aprovacao": "recuperacao"  }
    },
    
    // options 
    {
        "multi" : false,  // update only one document 
        "upsert" : false  // insert a new document, if no existing document match the query 
    }
);

# --> Remover / excluir um documents
## 
db.getCollection('JAVA').remove({ "aluno.nome":"fernanda" });


# --> Consulta por projeção
## 
db.getCollection('JAVA').find({}, {"aprovacao" : 1 , "_id" : 0 })

# --> Consulta utilizando selectores
## 
db.getCollection('JAVA').find({$or: [ { "aluno.nome": /.*fernan.*/ , "aprovacao":"aprovado" } ]})

# --> Consulta paginada e ordenada (ignorar)
## 
db.getCollection('JAVA').find({}).skip(1)

# --> Consulta paginada e ordenada (classificar - ordem decrescente)
## 
db.getCollection('JAVA').find().sort( { "nota final": -1 } )

# --> Consulta paginada e ordenada (classificar - ordem crescente)
## 
db.getCollection('JAVA').find().sort( { "nota final": 1 } )

# --> Consulta paginada e ordenada (limitar)
## 
db.getCollection('JAVA').aggregate([{ $limit:2}])

## Sempre avante! Confia!!! 🚀🚀🚀🚀
