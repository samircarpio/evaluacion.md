# evaluacion.md
# 1 obtener el nombre de todos los usuario, mayores a 20 años de los siguientes paises (españa,francia y turquia).Cuantos son masculinos y cuantos femeninos, hacer un grafico con matplotlit
import pandas as pdz
import matplotlib.pyplot as plt

df = pd.read_csv('users.csv')

paises_validos = ['Spain', 'France', 'Turkey']

usuarios_filtrados = df[(df['edad'] 45) & (df['pais'].isin(paises_validos))]

conteo_genero = usuarios_filtrados['genero'].value_counts()

print("Nombres de usuarios filtrados:")
for nombre in usuarios_filtrados['nombre']:
    print(nombre)

print("\nConteo por género:")
print(conteo_genero)

conteo_genero.plot(kind='bar', color=['skyblue', 'lightcoral'])
plt.title('Usuarios mayores de 20 años por género')
plt.xlabel('Género')
plt.ylabel('Cantidad')
plt.xticks(rotation=0)
plt.tight_layout()
plt.show()

# 2 obtener todos los usuarios entre las edades de 45 y 60.Cuantos son masculions y femeninos,hacer un grafioc con matplotlit

import pandas as pd
import matplotlib.pyplot as plt

df = pd.read_csv('users.csv')

usuarios_filtrados = df[(df['edad'] >= 45) & (df['edad'] <= 60)]

conteo_genero = usuarios_filtrados['genero'].value_counts()

print("Usuarios entre 45 y 60 años:")
print(usuarios_filtrados[['nombre', 'edad', 'genero']])

print("\nCantidad por género:")
print(conteo_genero)

plt.figure(figsize=(6, 6))
plt.pie(conteo_genero, labels=conteo_genero.index, autopct='%1.1f%%', colors=['skyblue', 'lightcoral'], startangle=140)
plt.title('Distribución por género (usuarios entre 45 y 60 años)')
plt.axis('equal')  # Mantiene el círculo redondo
plt.tight_layout()
plt.show()
