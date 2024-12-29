import json

# Dados fictícios sobre frutas, armas e habilidades no Blox Fruits
fruits_data = [
    {
        "name": "Bomb",
        "type": "Common",
        "cost": 5000,
        "abilities": ["Bomb Explosion", "Self Destruction"],
        "damage": 500
    },
    {
        "name": "Flame",
        "type": "Rare",
        "cost": 250000,
        "abilities": ["Fire Bullets", "Flame Flight", "Fire Tornado"],
        "damage": 1500
    },
    {
        "name": "Ice",
        "type": "Rare",
        "cost": 350000,
        "abilities": ["Ice Spears", "Ice Skating", "Ice Dragon"],
        "damage": 1400
    },
    {
        "name": "Dragon",
        "type": "Mythical",
        "cost": 3500000,
        "abilities": ["Dragon Breath", "Dragon Flight", "Dragon Meteor"],
        "damage": 3000
    }
]

weapons_data = [
    {
        "name": "Katana",
        "type": "Sword",
        "damage": 200,
        "cost": 1000
    },
    {
        "name": "Pole",
        "type": "Spear",
        "damage": 450,
        "cost": 100000
    }
]

locations_data = [
    {"name": "Pirate Starter Island", "level_range": "1-10", "items": ["Chests"]},
    {"name": "Jungle", "level_range": "15-30", "items": ["Chests", "Fruits"]},
    {"name": "Skylands", "level_range": "150-200", "items": ["Rare Weapons"]}
]

def list_fruits():
    print("=== Lista de Frutas Disponíveis ===")
    for fruit in fruits_data:
        print(f"- {fruit['name']} ({fruit['type']}) - Custo: ${fruit['cost']}")

def fruit_details(fruit_name):
    fruit = next((f for f in fruits_data if f['name'].lower() == fruit_name.lower()), None)
    if fruit:
        print(f"\n=== Detalhes da Fruta: {fruit['name']} ===")
        print(f"Tipo: {fruit['type']}")
        print(f"Custo: ${fruit['cost']}")
        print(f"Dano Base: {fruit['damage']}")
        print("Habilidades:")
        for ability in fruit['abilities']:
            print(f"  - {ability}")
    else:
        print("\nFruta não encontrada. Verifique o nome e tente novamente.")

def calculate_damage(level, mastery, fruit_name):
    fruit = next((f for f in fruits_data if f['name'].lower() == fruit_name.lower()), None)
    if fruit:
        base_damage = fruit['damage']
        total_damage = base_damage + (level * 10) + (mastery * 5)
        print(f"\n=== Cálculo de Dano para {fruit['name']} ===")
        print(f"Nível: {level}, Maestria: {mastery}")
        print(f"Dano Total: {total_damage}")
    else:
        print("\nFruta não encontrada. Verifique o nome e tente novamente.")

def list_weapons():
    print("=== Lista de Armas Disponíveis ===")
    for weapon in weapons_data:
        print(f"- {weapon['name']} ({weapon['type']}) - Dano: {weapon['damage']} - Custo: ${weapon['cost']}")

def location_details():
    print("=== Localizações Disponíveis ===")
    for location in locations_data:
        print(f"- {location['name']} (Níveis: {location['level_range']})")
        print(f"  Itens Encontrados: {', '.join(location['items'])}")

def main():
    while True:
        print("\n=== Bem-vindo ao Guia Completo do Blox Fruits ===")
        print("1. Listar todas as frutas")
        print("2. Detalhes de uma fruta")
        print("3. Calcular dano de uma fruta")
        print("4. Listar todas as armas")
        print("5. Exibir localizações e itens")
        print("6. Sair")

        choice = input("Escolha uma opção: ")

        if choice == "1":
            list_fruits()
        elif choice == "2":
            fruit_name = input("Digite o nome da fruta: ")
            fruit_details(fruit_name)
        elif choice == "3":
            fruit_name = input("Digite o nome da fruta: ")
            level = int(input("Digite o seu nível: "))
            mastery = int(input("Digite a maestria da fruta: "))
            calculate_damage(level, mastery, fruit_name)
        elif choice == "4":
            list_weapons()
        elif choice == "5":
            location_details()
        elif choice == "6":
            print("Saindo do guia. Aproveite o jogo!")
            break
        else:
            print("Opção inválida. Tente novamente.")

if __name__ == "__main__":
    main()
