**Cours de Bases de Données Avancées (B.D.A)**

**Objectif du cours**

-   Maitriser la conception et la realisation d'une BD
-   Intrrogation d'une BD

**Déroulement du cours**
-
-   Séannces de cours magistraux
-   Tp devoire surveiller

**Contenu du cours**

1.  Définition préliminaires
2.  Modele entité-association (E/A)
3.  Model relationnel
4.  Paasage du model  E/A au modele relationnel

I. _**Une base de donnée:**_ c'est un ensemble de données _structurés_ mis à la disposition d'un ensemble d'utilisateur.
(Permettre de centraliser les données)

2.Systeme de Gestion de baases de données (SGBD): c'est une application qui facilite la gestion d'une B.D. Il existe plusieurs SGBD sur le marche: 

-SQL Server (Microsoft)

-MySQL (Sun => oracle)

-Posgres SQL (  )

-Maria DB (??)

-Oracle (Oracle)
-etc

**Chapitre2**
II. Le modele Entité-Association(E/A)

**Model:** C'est une représentation abstraite de la réalité

Le modele E/A aussi appelé modele conceptuel de données (MCD) permet de concevoire une base de donnée

1.Conccepts de base:

1.1 Entité:
C'est une ensemble _homogéne_ d'objets

1.2 Association:C'est une lien sémantique entre une ou plusieurs entité

|Client     |CompteBancaire|
|------     |--------------|
|------     |--------------|
|------     |--------------|

1.3 **Attribut**: Un attribut ou une proprieté est une caracteristique d'une **entité** ou d'une **association**

1.4 **Identifiant**: C'est un attribut qui permet d'identifier de maniere unique un objet de l'entité.

1.5 **_Cardinalité_** : C'est un couple de valeurs min,max qui permet  de determiner le nombre minimal et le nombre maximal de fois qu'un objet de l'entité est concerné par l'association.

Un client peut posséder combien de compte client=> 1,n

Un compte Bancaire peut etre posséder par 1 et 1 seule client
 
 **_2. Regle de validation:_**
 
 Vérifier la validité d'un modéle E/A revient à vérifier si toutes dépendances fonctionnelles sont correctes.
 
 **2.1Dépendance Fonctionnelle(DF):**
 
 **A.Définition:** C'est une implication mathématique de la forme a->b 
 
 a->b (se lit a determine b)
 **B.Types de DF:** 
 *  **DF intra-entité:** L'identifiant d'une entité determine chaque attribut de cette meme entité.
 
 _Exemple_:NumCompte->solde
 
 NumCompte->type
 *  **DF intra**: La composition des identifiants des entités concernées par une association détermine chaque attribut de cette meme association.
 
 _Exemple_:
            
            Commande  1,n                                  0,n  Produit
                                   contenir/quantitéCOm
            Commande numCommande dateComm                 Produit reference libelle PU
    N°commande,reference->quantitéCom
            
 
*   **DF forte**: L'identifiant du coté de la cardinalité 1,1 determine l'identifiant de l'autre entité

_Exmple:_
    
        N°Compte->N°Piece  (Si je connais le numéro du compte je connais le client)
   
*   **DF faible**: 

_Exemple:_

        Personne 0,1                                    1,1Vote
        N°piece                                         NumVote
        Nom                                             DateVote
        Prenom
        
        N°piece->NumVote est D.F faible  (Pas tjrs vraie)
        NumVote->N°piece  est une D.F forte (Tjrs vraie)
        
**_C.  Proprietes sur les D.F.s:_**

a->b et b->c alors a->c (_La transitivité_)

_Exemple:_
        
        Employee 0,1          travailler      1,n   Departement         appartenir       1,n Direction
        Matricule                                   N°dept                                   N°Dir         
        Nom                                         Nomdept                                  NomDir
        Prenom
                                     
        1°) mattricule->N°dept
        2°)N°dept ->N°dir
        

a->b et b, truc->c alors a, truc->c(Pseudo transitivité)

**_2.2 Exercice d'applcation:_** Modélisation d'une base de données commerciale

    Client                                   Article
    N°Client                                 reference
    Nom                                      libelle  
    prenom                                        0,n
    
    1,n
    
    passer
                1,1    Commande  1,n
                     NCommande                  concerner                                         
                     date                         qtCommandé,PrixVente
     
     1) N°commande -> N°client
                et
     2) N°client,reference -> PVente
                alors
        N°commande,reference -> pVente

     

    
Sauvegarder
    
        lx4gm0n        