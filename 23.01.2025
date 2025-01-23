import pandas as pd


df_excel = pd.read_excel("Ядики XLSX.xlsx")

def display_menu():
    print("\nМеню:")
    print("1. Вывести весь дата сет")
    print("2. Вывести конкретную строку по индексу")
    print("3. Вывести столбец по индексу")
    print("4. Вывести ячейку по индексу")
    print("5. Среднее арифметическое ячеек")
    print("6. Выход")

def calculate_average(value):
    if isinstance(value, (int, float)):
        return value
    else:
        raise ValueError("Значение в ячейке не является числом.")

def main():

    if df_excel is None:
        return

    while True:
        display_menu()
        choice = input("Выберите опцию (1-6): ")

        if choice == '1':
            print("\nВесь дата сет:")
            print(df_excel)

        elif choice == '2':
            index = int(input("Введите индекс строки: "))
            if 0 <= index < len(df_excel):
                print("\nСтрока по индексу", index, ":")
                print(df_excel.iloc[index])
            else:
                print("Индекс вне диапазона.")

        elif choice == '3':
            index = int(input("Введите индекс столбца: "))
            if 0 <= index < df_excel.shape[1]:
                print("\nСтолбец по индексу", index, ":")
                print(df_excel.iloc[:, index])
            else:
                print("Индекс вне диапазона.")

        elif choice == '4':
            row_index = int(input("Введите индекс строки: "))
            col_index = int(input("Введите индекс столбца: "))
            if 0 <= row_index < len(df_excel) and 0 <= col_index < df_excel.shape[1]:
                cell_value = df_excel.iat[row_index, col_index]
                print(f"\nЯчейка ({row_index}, {col_index}): {cell_value}")

                action = input("Выберите действие с ячейкой (1 - изменить, 2 - удалить, 3 - создать новую ячейку): ")
                if action == '1':
                    new_value = input("Введите новое значение: ")
                    df_excel.iat[row_index, col_index] = new_value
                    print("Ячейка изменена.")
                elif action == '2':
                    df_excel.iat[row_index, col_index] = None
                    print("Ячейка удалена.")
                elif action == '3':
                    new_value = input("Введите значение для новой ячейки: ")
                    df_excel.loc[row_index, df_excel.columns[col_index]] = new_value
                    print("Новая ячейка создана.")
                else:
                    print("Неверный выбор действия.")
            else:
                print("Индексы вне диапазона.")

        elif choice == '5':
            row_index = int(input("Введите индекс строки: "))
            col_index = int(input("Введите индекс столбца: "))
            if 0 <= row_index < len(df_excel) and 0 <= col_index < df_excel.shape[1]:
                cell_value = df_excel.iat[row_index, col_index]
                try:
                    average = calculate_average(cell_value)
                    print(f"Среднее арифметическое значения в ячейке ({row_index}, {col_index}): {average}")
                except ValueError as e:
                    print(e)
                    print("Пожалуйста, укажите другую ячейку.")
            else:
                print("Индексы вне диапазона.")

        elif choice == '6':
            df_excel.to_xlsx("Ядики XLSX.xlsx", index=False)
            print("Изменения сохранены. Выход из программы.")
            break

        else:
            print("Неверный выбор. Пожалуйста, выберите от 1 до 5.")


if __name__ == "__main__":
    main()

import openpyxl
