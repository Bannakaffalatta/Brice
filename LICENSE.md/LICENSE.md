def pyramide(n):
    """
        Affiche une pyramide de 'O' dont la hauteur est entrée en paramètre
        
        :param n: (int) Hauteur de la pyramide
        :return: (None)
        
        CU : n >= 0
        
        Exemples :
        
        >>> pyramide(5)
            O
           O O
          O   O
         O     O       
        OOOOOOOOO
        
        >>> pyramide(7)
              O
             O O
            O   O
           O     O
          O       O
         O         O
        OOOOOOOOOOOOO
        
        >>> pyramide(-1)
        Traceback (most recent call last):
        ...
        AssertionError: Il faut que le paramètre soit supérieur ou égal à 0.
            
    """
    
    assert n >= 0, "Il faut que le paramètre soit supérieur ou égal à 0."   
    
    Droite = ""
    Gauche = ''
    Alinea = ''
    Ecart = ''
    f = 0
    c = 1
    
    for i in range(1, n):
        p = i
        while p < n:
            Alinea = Alinea + ' '
            p = p + 1
        
        Gauche = Alinea + 'O'
       
        if i == 1:
            print(Gauche)
            
        else:
            while f < c:
                Ecart = Ecart + ' '
                f += 1
                
            c = f + 2
            Droite =  Ecart + 'O' + Alinea
            print(Gauche + Droite)
            
        Droite = ''
        Gauche = ''
        Alinea = ''
        
    afficher_ligne(2*n-1)
    
    return None
    
    
    
    def jeu():
    """
        Procédure permettant de jouer au jeu du plus petit au plus grand. Le but est de trouver le nombre choisit aléatoirement en 8 tentative.
        
        CU : Aucune
        
        Exemples :
        
        Pas d'exemple possible.
    """
    
    N = randint(1, 100)
    P = int(input('Choisissez un nombre compris entre 1 et 100 :'))
    T = 6                                                             # T est la variable qui compte le nombre de tenative. Elle est égal à ('Nombre de tentative souhaité' -1)

    while P != N and P != 0 and T != 0:
        if P > N:
            print('Votre nombre est trop grand')
            T -= 1
        else:
            print('Votre nombre est trop petit')
            T -= 1
        P = int(input('Choisissez un nombre compris entre 1 et 100 :'))
        
    if P == N:
        print('Gagné !')
    
    else:
        print('Perdu ! Le nombre était :', N)
        
        
        
def jeu_ordi():
    """
        Procédure permettant de jouer au jeu du nombre mystère avec l'ordinateur. Celui-ci doit deviner le nombre auquel vous pensez (Nombre entré en paramètre)
        
        CU : Aucune
        
        Exemples :
        
        Pas d'exemple possible.
        
    """    
    P = randint(1, 100)
    R = ''
    Max = 101
    Min = 0
    T = False
    
    print(P)
    
    while not T:
        
        R = input('Es-ce plus ou moins grand ? ')
        
        if R == '+':
            Max = P
            
            if Min+1 > Max-1:
                print('\nAbandon')
                T = True
                
            else:
                P = randint(Min+1, Max-1)
                print(P)
           
           
        elif R == '-':
            Min = P
            
            if Min+1 > Max-1:
                print('\nAbandon')
                T = True
                
            else:
                P = randint(Min+1, Max-1)
                print(P)
            
        elif R == '!':
            print('\nGagné !')
            T = True
