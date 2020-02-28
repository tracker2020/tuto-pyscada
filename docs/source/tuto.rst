Introduction
============

Sur Pyscada, un système de vue est instauré. Une vue englobe des pages et ces pages contiennent le contenu que l'on souhaite afficher.

Ci dessous le choix des vues lorsque l'on s'est connecté à notre compte:

		.. image:: pic/choix_vue.PNG
		
Et lorsque l'on clique sur la Vue 1:

		.. image:: pic/page.PNG
		

Pour modifier l'interface sur Pyscada, on entre d'abord l'adresse ip de celle-ci sur la barre de recherche web. Il faut ensuite se connecter à notre compte.


Une fois connecté, la modification est accessible via la partie **Admin**:

		.. image:: pic/admin.PNG
		


Créer une vue
=================
Pour créer une vue il suffit de cliquer sur **Add** view :

		.. image:: pic/view.png

Ensuite insérez le titre de la vue, puis les pages qu'elle contiendra. Chaque élément créé est modifiable par la suite, on pourra donc ajouter des pages après avoir créé la vue.

		.. image:: pic/add_view.PNG

Cliquez ensuite sur **Save** et la vue sera créée.



Créer une page
===================

Dans la page d'accueil admin, cliquez sur **Add** dans la ligne page, puis remplissez les paramètres de votre page et cliquez sur **Save**:

		.. image:: pic/add_page.PNG
		
Créer un control item et un control panel
=========================================

Un control item sert à lire ou à écrire une valeur de variable que l'on a créé auparavant. Le control panel sert à afficher ou non sur l'interface utilisateur la valeur du control item.

Pour créer un control item, cliquez sur **Add** dans la ligne control item dans la page d'accueil.
Cette page s'affiche:

				.. image:: pic/add_control_item.PNG
				
Voici l'exemple de nos controls items:

				.. image:: pic/control_item.PNG
				
Pour créer un control panel:

				.. image:: pic/control_panel.PNG


Créer un graphique
==================

Dans la page d'accueil, cliquez sur **Add** dans la ligne *charts*, puis ajoutez les variables qu'il y aura sur le graphique.

		.. image:: pic/add_chart.PNG
		
Exemple du rendu d'un graphique: Température en fonction du temps.

		.. image:: pic/exemple_graphique.PNG
		
Modélisation de la page
=======================

Une fois que les éléments sont créés, l'outil Widget sera nécessaire pour choisir ce qui apparaitra sur l'interface utilisateur.

		.. image:: pic/Widget.PNG
		
Cette page permet d'afficher les controls items définis précédemment. On définit la rangée, la colonne et la taille du contenu qui sera affiché.

		.. image:: pic/add_widget.PNG
		

Réalisation d'un script
=======================

Sur Pyscada
^^^^^^^^^^^

Pour interagir avec l'interface les scripts sont nécessaires. Ils serviront à lire ou à écrire des données dans putty et donc sur la carte. Nous allons prendre l'exemple de la création d'un bouton.
Allez dans la page d'accueil Admin, cliquez sur **Add** dans la ligne script qui se situe plus bas dans la page.

		.. image:: pic/pyscada_scripting.PNG

Complétez ensuite les paramètres du script:

		.. image:: pic/add_scripting.PNG
		
Sur putty
^^^^^^^^^
Voici l'exemple du programme de script pour putty:

		.. image:: pic/script_putty.PNG

Sous forme txt pour copier coller::

	$from time import time
	import logging
	import smbus
	
	#logger = logging.getLogger(__name__)
	
	def startup(self):
		"""
		write your code startup code here, don't change the name of this function
		:return:
		"""
		pass
	
	def shutdown(self):
		"""
		write your code shutdown code here, don't change the name of this function
		:return:
		"""
		pass
	
	def script(self):
	
		data = self.read_values_from_db(variable_names=['bouton2'], current_value_only=True)
		#logger.debug(bouton2)
		bus = smbus.SMBus(1)
		bus.close()
		
Le programme est le même pour chaque script que nous avons créé, la seule partie modifiable se situe après la ligne def script(self).
La ligne #logger.debug(bouton2) permet de voir les logs du script lorsque l'on enlève le # du programme.


