# LZ6
# Лабораторна робота №6: Використання вказівників
**Виконав:** студентка групи 4СОМ, Крамар Анна (Варіант № 4)

## Завдання.
<img width="730" height="324" alt="image" src="https://github.com/user-attachments/assets/dceeeaaf-d42a-4b21-afc3-ec0581a9dd91" />
<img width="616" height="253" alt="image" src="https://github.com/user-attachments/assets/6e8b50c0-d9de-4c85-90e8-f2f992cafe81" />

### 💻 Результати коду програми:
<img width="705" height="448" alt="image" src="https://github.com/user-attachments/assets/3c80824a-6462-4d83-9fc8-b33f04d47d42" />
<img width="670" height="441" alt="image" src="https://github.com/user-attachments/assets/3bcc0951-56a5-4ad5-a3b6-c00b87ee9e74" />
<img width="713" height="442" alt="image" src="https://github.com/user-attachments/assets/f5b75ba5-932a-4f70-b677-8cebf9f8c005" />

### Основний код програми:
```cpp
private: System::Void button1_Click(System::Object^ sender, System::EventArgs^ e) {
      double t1, t2, t3, t4, t5, t6;
    
      if (!Double::TryParse(textBox1->Text, t1) ||
        !Double::TryParse(textBox2->Text, t2) ||
        !Double::TryParse(textBox3->Text, t3) ||
        !Double::TryParse(textBox4->Text, t4) ||
        !Double::TryParse(textBox5->Text, t5) ||
        !Double::TryParse(textBox6->Text, t6))
      {
        MessageBox::Show("Введіть числа (час у секундах)! \n"+
        "Або заповніть всі поля.\n"+
        "Також зауважте, що час має бути лише додатнім значенням.");
        return;
      }
    
      if (t1 <= 0 || t2 <= 0 || t3 <= 0 || t4 <= 0 || t5 <= 0 || t6 <= 0)
      {
        MessageBox::Show("Час має бути більшим за 0!");
        return;
      }
    
      double arr[6];
      double* ptr = arr;
    
      arr[0] = t1;
      arr[1] = t2;
      arr[2] = t3;
      arr[3] = t4;
      arr[4] = t5;
      arr[5] = t6;
    
      double sum = 0;
      for (int i = 0; i < 6; i++) {
        sum += *(ptr + i);
      }
      double avg = sum / 6;
    
    
      double best = *ptr;
      double worst = *ptr;
      int best_num = 1;
    
      for (int i = 1; i < 6; i++) {
        if (*(ptr + i) < best) {
          best = *(ptr + i);
          best_num = i + 1;
        }
        if (*(ptr + i) > worst) {
          worst = *(ptr + i);
        }
      }
    
    
      int count_better = 0;
      for (int i = 0; i < 6; i++) {
        if (*(ptr + i) < avg) {
          count_better++;
        }
      }
    
      label8->Text =
        "Найкращий результат: " + best + " c\n" +
        "Найгірший результат: " + worst + " c\n" +
        "Середній час: " + Math::Round(avg, 2) + " c\n" +
        "Кращі за середній: " + count_better + " уч.\n" +
        "Номер переможця: " + best_num + "\n\n" +
        "Пояснення: найкращий результат — найменший час,\n" +
        "найгірший — найбільший. Кращим за середній вважається\n" +
        "учасник, чий час менший за середній.";
	}
private: System::Void button2_Click(System::Object^ sender, System::EventArgs^ e) {
        textBox1->Clear();
        textBox2->Clear();
        textBox3->Clear();
        textBox4->Clear();
        textBox5->Clear();
        textBox6->Clear();
        label8->Text = "";
        textBox1->Focus();
 }
```
### Висновок.
  Лабораторну виконано успішно. 
  
  У ході лабораторної роботи було створено застосунок Windows Forms на C++/CLI для аналізу результатів бігу шести учасників (варіант 4). Програма приймає час кожного учасника в секундах,   перевіряє коректність введених даних за допомогою TryParse та визначає найкращий і найгірший результати, середній час, кількість учасників із результатом кращим за середній і номер переможця.
  
  Дані зберігаються в масиві, а всі обчислення виконуються через вказівник double* ptr за допомогою розіменування *(ptr + i), що дозволило закріпити навички роботи з вказівниками в C++.   Результати та коротке пояснення виводяться на форму в мітку label8.

  Також було використано Math::Round(avg, 2) для округлання avg до 2 цифр після коми.
  
  Для повторного виконання обчислень без перезапуску програми додано кнопку «Очистити», яка скидає всі поля введення та область результатів.
  
  Файли додано в цей репозиторій. Щоб виконати завдання, використовувала приклади з файлу лабораторної 6.
