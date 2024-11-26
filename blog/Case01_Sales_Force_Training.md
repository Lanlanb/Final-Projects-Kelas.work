<a href="https://colab.research.google.com/github/Lanlanb/Final-Projects-Kelas.work/blob/main/Case01_Sales_Force_Training.ipynb" target="_parent"><img src="https://colab.research.google.com/assets/colab-badge.svg" alt="Open In Colab"/></a>

# **Case Study 01: Sales Force Training**

**Overview dan Background Problems**

Perusahaan X ingin meningkatkan penjualan mereka. Dari data penjualan sebelumnya menunjukkan bahwa penjualan rata-rata yaitu $100 per transaksi. Setelah melakukan training kepada pekerja sales, data penjualan terbaru (yang diambil dari 25 sampel pekerja sales) tersimpan dalam tabel data di bawah ini :


```python
df
```





  <div id="df-5a586b7e-8c62-4acd-a29e-1e9af3ca791f" class="colab-df-container">
    <div>
<style scoped>
    .dataframe tbody tr th:only-of-type {
        vertical-align: middle;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }

    .dataframe thead th {
        text-align: right;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>TransactionAmount</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>100</td>
    </tr>
    <tr>
      <th>1</th>
      <td>150</td>
    </tr>
    <tr>
      <th>2</th>
      <td>50</td>
    </tr>
    <tr>
      <th>3</th>
      <td>100</td>
    </tr>
    <tr>
      <th>4</th>
      <td>130</td>
    </tr>
    <tr>
      <th>5</th>
      <td>120</td>
    </tr>
    <tr>
      <th>6</th>
      <td>100</td>
    </tr>
    <tr>
      <th>7</th>
      <td>85</td>
    </tr>
    <tr>
      <th>8</th>
      <td>70</td>
    </tr>
    <tr>
      <th>9</th>
      <td>150</td>
    </tr>
    <tr>
      <th>10</th>
      <td>150</td>
    </tr>
    <tr>
      <th>11</th>
      <td>120</td>
    </tr>
    <tr>
      <th>12</th>
      <td>50</td>
    </tr>
    <tr>
      <th>13</th>
      <td>100</td>
    </tr>
    <tr>
      <th>14</th>
      <td>100</td>
    </tr>
    <tr>
      <th>15</th>
      <td>140</td>
    </tr>
    <tr>
      <th>16</th>
      <td>90</td>
    </tr>
    <tr>
      <th>17</th>
      <td>150</td>
    </tr>
    <tr>
      <th>18</th>
      <td>50</td>
    </tr>
    <tr>
      <th>19</th>
      <td>90</td>
    </tr>
    <tr>
      <th>20</th>
      <td>120</td>
    </tr>
    <tr>
      <th>21</th>
      <td>100</td>
    </tr>
    <tr>
      <th>22</th>
      <td>110</td>
    </tr>
    <tr>
      <th>23</th>
      <td>75</td>
    </tr>
    <tr>
      <th>24</th>
      <td>65</td>
    </tr>
  </tbody>
</table>
</div>
    <div class="colab-df-buttons">

  <div class="colab-df-container">
    <button class="colab-df-convert" onclick="convertToInteractive('df-5a586b7e-8c62-4acd-a29e-1e9af3ca791f')"
            title="Convert this dataframe to an interactive table."
            style="display:none;">

  <svg xmlns="http://www.w3.org/2000/svg" height="24px" viewBox="0 -960 960 960">
    <path d="M120-120v-720h720v720H120Zm60-500h600v-160H180v160Zm220 220h160v-160H400v160Zm0 220h160v-160H400v160ZM180-400h160v-160H180v160Zm440 0h160v-160H620v160ZM180-180h160v-160H180v160Zm440 0h160v-160H620v160Z"/>
  </svg>
    </button>

  <style>
    .colab-df-container {
      display:flex;
      gap: 12px;
    }

    .colab-df-convert {
      background-color: #E8F0FE;
      border: none;
      border-radius: 50%;
      cursor: pointer;
      display: none;
      fill: #1967D2;
      height: 32px;
      padding: 0 0 0 0;
      width: 32px;
    }

    .colab-df-convert:hover {
      background-color: #E2EBFA;
      box-shadow: 0px 1px 2px rgba(60, 64, 67, 0.3), 0px 1px 3px 1px rgba(60, 64, 67, 0.15);
      fill: #174EA6;
    }

    .colab-df-buttons div {
      margin-bottom: 4px;
    }

    [theme=dark] .colab-df-convert {
      background-color: #3B4455;
      fill: #D2E3FC;
    }

    [theme=dark] .colab-df-convert:hover {
      background-color: #434B5C;
      box-shadow: 0px 1px 3px 1px rgba(0, 0, 0, 0.15);
      filter: drop-shadow(0px 1px 2px rgba(0, 0, 0, 0.3));
      fill: #FFFFFF;
    }
  </style>

    <script>
      const buttonEl =
        document.querySelector('#df-5a586b7e-8c62-4acd-a29e-1e9af3ca791f button.colab-df-convert');
      buttonEl.style.display =
        google.colab.kernel.accessAllowed ? 'block' : 'none';

      async function convertToInteractive(key) {
        const element = document.querySelector('#df-5a586b7e-8c62-4acd-a29e-1e9af3ca791f');
        const dataTable =
          await google.colab.kernel.invokeFunction('convertToInteractive',
                                                    [key], {});
        if (!dataTable) return;

        const docLinkHtml = 'Like what you see? Visit the ' +
          '<a target="_blank" href=https://colab.research.google.com/notebooks/data_table.ipynb>data table notebook</a>'
          + ' to learn more about interactive tables.';
        element.innerHTML = '';
        dataTable['output_type'] = 'display_data';
        await google.colab.output.renderOutput(dataTable, element);
        const docLink = document.createElement('div');
        docLink.innerHTML = docLinkHtml;
        element.appendChild(docLink);
      }
    </script>
  </div>


<div id="df-87f2df45-1237-4bc8-b7d6-84263849b4de">
  <button class="colab-df-quickchart" onclick="quickchart('df-87f2df45-1237-4bc8-b7d6-84263849b4de')"
            title="Suggest charts"
            style="display:none;">

<svg xmlns="http://www.w3.org/2000/svg" height="24px"viewBox="0 0 24 24"
     width="24px">
    <g>
        <path d="M19 3H5c-1.1 0-2 .9-2 2v14c0 1.1.9 2 2 2h14c1.1 0 2-.9 2-2V5c0-1.1-.9-2-2-2zM9 17H7v-7h2v7zm4 0h-2V7h2v10zm4 0h-2v-4h2v4z"/>
    </g>
</svg>
  </button>

<style>
  .colab-df-quickchart {
      --bg-color: #E8F0FE;
      --fill-color: #1967D2;
      --hover-bg-color: #E2EBFA;
      --hover-fill-color: #174EA6;
      --disabled-fill-color: #AAA;
      --disabled-bg-color: #DDD;
  }

  [theme=dark] .colab-df-quickchart {
      --bg-color: #3B4455;
      --fill-color: #D2E3FC;
      --hover-bg-color: #434B5C;
      --hover-fill-color: #FFFFFF;
      --disabled-bg-color: #3B4455;
      --disabled-fill-color: #666;
  }

  .colab-df-quickchart {
    background-color: var(--bg-color);
    border: none;
    border-radius: 50%;
    cursor: pointer;
    display: none;
    fill: var(--fill-color);
    height: 32px;
    padding: 0;
    width: 32px;
  }

  .colab-df-quickchart:hover {
    background-color: var(--hover-bg-color);
    box-shadow: 0 1px 2px rgba(60, 64, 67, 0.3), 0 1px 3px 1px rgba(60, 64, 67, 0.15);
    fill: var(--button-hover-fill-color);
  }

  .colab-df-quickchart-complete:disabled,
  .colab-df-quickchart-complete:disabled:hover {
    background-color: var(--disabled-bg-color);
    fill: var(--disabled-fill-color);
    box-shadow: none;
  }

  .colab-df-spinner {
    border: 2px solid var(--fill-color);
    border-color: transparent;
    border-bottom-color: var(--fill-color);
    animation:
      spin 1s steps(1) infinite;
  }

  @keyframes spin {
    0% {
      border-color: transparent;
      border-bottom-color: var(--fill-color);
      border-left-color: var(--fill-color);
    }
    20% {
      border-color: transparent;
      border-left-color: var(--fill-color);
      border-top-color: var(--fill-color);
    }
    30% {
      border-color: transparent;
      border-left-color: var(--fill-color);
      border-top-color: var(--fill-color);
      border-right-color: var(--fill-color);
    }
    40% {
      border-color: transparent;
      border-right-color: var(--fill-color);
      border-top-color: var(--fill-color);
    }
    60% {
      border-color: transparent;
      border-right-color: var(--fill-color);
    }
    80% {
      border-color: transparent;
      border-right-color: var(--fill-color);
      border-bottom-color: var(--fill-color);
    }
    90% {
      border-color: transparent;
      border-bottom-color: var(--fill-color);
    }
  }
</style>

  <script>
    async function quickchart(key) {
      const quickchartButtonEl =
        document.querySelector('#' + key + ' button');
      quickchartButtonEl.disabled = true;  // To prevent multiple clicks.
      quickchartButtonEl.classList.add('colab-df-spinner');
      try {
        const charts = await google.colab.kernel.invokeFunction(
            'suggestCharts', [key], {});
      } catch (error) {
        console.error('Error during call to suggestCharts:', error);
      }
      quickchartButtonEl.classList.remove('colab-df-spinner');
      quickchartButtonEl.classList.add('colab-df-quickchart-complete');
    }
    (() => {
      let quickchartButtonEl =
        document.querySelector('#df-87f2df45-1237-4bc8-b7d6-84263849b4de button');
      quickchartButtonEl.style.display =
        google.colab.kernel.accessAllowed ? 'block' : 'none';
    })();
  </script>
</div>

  <div id="id_c8fee3d1-8d80-47b7-94e8-69df1048dea9">
    <style>
      .colab-df-generate {
        background-color: #E8F0FE;
        border: none;
        border-radius: 50%;
        cursor: pointer;
        display: none;
        fill: #1967D2;
        height: 32px;
        padding: 0 0 0 0;
        width: 32px;
      }

      .colab-df-generate:hover {
        background-color: #E2EBFA;
        box-shadow: 0px 1px 2px rgba(60, 64, 67, 0.3), 0px 1px 3px 1px rgba(60, 64, 67, 0.15);
        fill: #174EA6;
      }

      [theme=dark] .colab-df-generate {
        background-color: #3B4455;
        fill: #D2E3FC;
      }

      [theme=dark] .colab-df-generate:hover {
        background-color: #434B5C;
        box-shadow: 0px 1px 3px 1px rgba(0, 0, 0, 0.15);
        filter: drop-shadow(0px 1px 2px rgba(0, 0, 0, 0.3));
        fill: #FFFFFF;
      }
    </style>
    <button class="colab-df-generate" onclick="generateWithVariable('df')"
            title="Generate code using this dataframe."
            style="display:none;">

  <svg xmlns="http://www.w3.org/2000/svg" height="24px"viewBox="0 0 24 24"
       width="24px">
    <path d="M7,19H8.4L18.45,9,17,7.55,7,17.6ZM5,21V16.75L18.45,3.32a2,2,0,0,1,2.83,0l1.4,1.43a1.91,1.91,0,0,1,.58,1.4,1.91,1.91,0,0,1-.58,1.4L9.25,21ZM18.45,9,17,7.55Zm-12,3A5.31,5.31,0,0,0,4.9,8.1,5.31,5.31,0,0,0,1,6.5,5.31,5.31,0,0,0,4.9,4.9,5.31,5.31,0,0,0,6.5,1,5.31,5.31,0,0,0,8.1,4.9,5.31,5.31,0,0,0,12,6.5,5.46,5.46,0,0,0,6.5,12Z"/>
  </svg>
    </button>
    <script>
      (() => {
      const buttonEl =
        document.querySelector('#id_c8fee3d1-8d80-47b7-94e8-69df1048dea9 button.colab-df-generate');
      buttonEl.style.display =
        google.colab.kernel.accessAllowed ? 'block' : 'none';

      buttonEl.onclick = () => {
        google.colab.notebook.generateWithVariable('df');
      }
      })();
    </script>
  </div>

    </div>
  </div>




Tujuan:
1. Mengaplikasikan analisis dari uji statistika untuk menentukan apakah kita harus menolak atau menerima hipotesis nol (H₀) berdasarkan hasil uji.
2. Menilai apakah pelatihan sales force memiliki dampak signifikan terhadap rata-rata penjualan.

## Preparation


```python
# Import library dan package
import pandas as pd
import numpy as np
import scipy.stats as stats
import statistics
```


```python
# membuat dataframe
df = pd.DataFrame({'TransactionAmount' : [100, 150, 50, 100, 130, 120, 100, 85, 70, 150, 150, 120, 50, 100, 100, 140, 90, 150, 50, 90, 120, 100, 110, 75, 65]})

# melihat random data dari dataframe
df.sample(5)
```





  <div id="df-4a395601-8ee8-4498-8e8f-447e4e109db9" class="colab-df-container">
    <div>
<style scoped>
    .dataframe tbody tr th:only-of-type {
        vertical-align: middle;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }

    .dataframe thead th {
        text-align: right;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>TransactionAmount</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>9</th>
      <td>150</td>
    </tr>
    <tr>
      <th>4</th>
      <td>130</td>
    </tr>
    <tr>
      <th>22</th>
      <td>110</td>
    </tr>
    <tr>
      <th>24</th>
      <td>65</td>
    </tr>
    <tr>
      <th>5</th>
      <td>120</td>
    </tr>
  </tbody>
</table>
</div>
    <div class="colab-df-buttons">

  <div class="colab-df-container">
    <button class="colab-df-convert" onclick="convertToInteractive('df-4a395601-8ee8-4498-8e8f-447e4e109db9')"
            title="Convert this dataframe to an interactive table."
            style="display:none;">

  <svg xmlns="http://www.w3.org/2000/svg" height="24px" viewBox="0 -960 960 960">
    <path d="M120-120v-720h720v720H120Zm60-500h600v-160H180v160Zm220 220h160v-160H400v160Zm0 220h160v-160H400v160ZM180-400h160v-160H180v160Zm440 0h160v-160H620v160ZM180-180h160v-160H180v160Zm440 0h160v-160H620v160Z"/>
  </svg>
    </button>

  <style>
    .colab-df-container {
      display:flex;
      gap: 12px;
    }

    .colab-df-convert {
      background-color: #E8F0FE;
      border: none;
      border-radius: 50%;
      cursor: pointer;
      display: none;
      fill: #1967D2;
      height: 32px;
      padding: 0 0 0 0;
      width: 32px;
    }

    .colab-df-convert:hover {
      background-color: #E2EBFA;
      box-shadow: 0px 1px 2px rgba(60, 64, 67, 0.3), 0px 1px 3px 1px rgba(60, 64, 67, 0.15);
      fill: #174EA6;
    }

    .colab-df-buttons div {
      margin-bottom: 4px;
    }

    [theme=dark] .colab-df-convert {
      background-color: #3B4455;
      fill: #D2E3FC;
    }

    [theme=dark] .colab-df-convert:hover {
      background-color: #434B5C;
      box-shadow: 0px 1px 3px 1px rgba(0, 0, 0, 0.15);
      filter: drop-shadow(0px 1px 2px rgba(0, 0, 0, 0.3));
      fill: #FFFFFF;
    }
  </style>

    <script>
      const buttonEl =
        document.querySelector('#df-4a395601-8ee8-4498-8e8f-447e4e109db9 button.colab-df-convert');
      buttonEl.style.display =
        google.colab.kernel.accessAllowed ? 'block' : 'none';

      async function convertToInteractive(key) {
        const element = document.querySelector('#df-4a395601-8ee8-4498-8e8f-447e4e109db9');
        const dataTable =
          await google.colab.kernel.invokeFunction('convertToInteractive',
                                                    [key], {});
        if (!dataTable) return;

        const docLinkHtml = 'Like what you see? Visit the ' +
          '<a target="_blank" href=https://colab.research.google.com/notebooks/data_table.ipynb>data table notebook</a>'
          + ' to learn more about interactive tables.';
        element.innerHTML = '';
        dataTable['output_type'] = 'display_data';
        await google.colab.output.renderOutput(dataTable, element);
        const docLink = document.createElement('div');
        docLink.innerHTML = docLinkHtml;
        element.appendChild(docLink);
      }
    </script>
  </div>


<div id="df-6738b02e-d9d6-41c0-a4a4-d67c9e6032f0">
  <button class="colab-df-quickchart" onclick="quickchart('df-6738b02e-d9d6-41c0-a4a4-d67c9e6032f0')"
            title="Suggest charts"
            style="display:none;">

<svg xmlns="http://www.w3.org/2000/svg" height="24px"viewBox="0 0 24 24"
     width="24px">
    <g>
        <path d="M19 3H5c-1.1 0-2 .9-2 2v14c0 1.1.9 2 2 2h14c1.1 0 2-.9 2-2V5c0-1.1-.9-2-2-2zM9 17H7v-7h2v7zm4 0h-2V7h2v10zm4 0h-2v-4h2v4z"/>
    </g>
</svg>
  </button>

<style>
  .colab-df-quickchart {
      --bg-color: #E8F0FE;
      --fill-color: #1967D2;
      --hover-bg-color: #E2EBFA;
      --hover-fill-color: #174EA6;
      --disabled-fill-color: #AAA;
      --disabled-bg-color: #DDD;
  }

  [theme=dark] .colab-df-quickchart {
      --bg-color: #3B4455;
      --fill-color: #D2E3FC;
      --hover-bg-color: #434B5C;
      --hover-fill-color: #FFFFFF;
      --disabled-bg-color: #3B4455;
      --disabled-fill-color: #666;
  }

  .colab-df-quickchart {
    background-color: var(--bg-color);
    border: none;
    border-radius: 50%;
    cursor: pointer;
    display: none;
    fill: var(--fill-color);
    height: 32px;
    padding: 0;
    width: 32px;
  }

  .colab-df-quickchart:hover {
    background-color: var(--hover-bg-color);
    box-shadow: 0 1px 2px rgba(60, 64, 67, 0.3), 0 1px 3px 1px rgba(60, 64, 67, 0.15);
    fill: var(--button-hover-fill-color);
  }

  .colab-df-quickchart-complete:disabled,
  .colab-df-quickchart-complete:disabled:hover {
    background-color: var(--disabled-bg-color);
    fill: var(--disabled-fill-color);
    box-shadow: none;
  }

  .colab-df-spinner {
    border: 2px solid var(--fill-color);
    border-color: transparent;
    border-bottom-color: var(--fill-color);
    animation:
      spin 1s steps(1) infinite;
  }

  @keyframes spin {
    0% {
      border-color: transparent;
      border-bottom-color: var(--fill-color);
      border-left-color: var(--fill-color);
    }
    20% {
      border-color: transparent;
      border-left-color: var(--fill-color);
      border-top-color: var(--fill-color);
    }
    30% {
      border-color: transparent;
      border-left-color: var(--fill-color);
      border-top-color: var(--fill-color);
      border-right-color: var(--fill-color);
    }
    40% {
      border-color: transparent;
      border-right-color: var(--fill-color);
      border-top-color: var(--fill-color);
    }
    60% {
      border-color: transparent;
      border-right-color: var(--fill-color);
    }
    80% {
      border-color: transparent;
      border-right-color: var(--fill-color);
      border-bottom-color: var(--fill-color);
    }
    90% {
      border-color: transparent;
      border-bottom-color: var(--fill-color);
    }
  }
</style>

  <script>
    async function quickchart(key) {
      const quickchartButtonEl =
        document.querySelector('#' + key + ' button');
      quickchartButtonEl.disabled = true;  // To prevent multiple clicks.
      quickchartButtonEl.classList.add('colab-df-spinner');
      try {
        const charts = await google.colab.kernel.invokeFunction(
            'suggestCharts', [key], {});
      } catch (error) {
        console.error('Error during call to suggestCharts:', error);
      }
      quickchartButtonEl.classList.remove('colab-df-spinner');
      quickchartButtonEl.classList.add('colab-df-quickchart-complete');
    }
    (() => {
      let quickchartButtonEl =
        document.querySelector('#df-6738b02e-d9d6-41c0-a4a4-d67c9e6032f0 button');
      quickchartButtonEl.style.display =
        google.colab.kernel.accessAllowed ? 'block' : 'none';
    })();
  </script>
</div>

    </div>
  </div>





```python
# menyimpan sampel data ke google drive
file_path = '/content/drive/My Drive/Final Project Bootcamp Kelas.work by Kelas.com/case01_sales_training.csv'
df.to_csv(file_path, index=False)
```


```python
# mengakses google drive
from google.colab import drive
drive.mount('/content/drive')
```

    Mounted at /content/drive


## Uji Statistika

Ketika kita menangani data, baik dalam jumlah kecil maupun besar, kita umumnya menggunakan dua jenis analisis utama untuk memahaminya: Descriptive Statistics dan Inferential Statistics. Meskipun memiliki tujuan yang berbeda, keduanya saling melengkapi.

Langkah pertama adalah menggunakan descriptive statistics untuk memberikan gambaran ringkas tentang data yang ada. Setelah itu, inferential statistics digunakan untuk menarik kesimpulan atau melakukan pengujian guna mengetahui apakah temuan dari data tersebut berlaku untuk konteks yang lebih luas. Dalam kasus ini, kita ingin mengevaluasi apakah program pelatihan sales berhasil meningkatkan penjualan di perusahaan X, maka kita akan menerapkan kedua jenis analisis ini.

### Descriptive Statistics

#### Measure of central tendency


```python
# measure of central tendency

mean_after = statistics.mean(df['TransactionAmount'])
percentage_increase = ((mean_after - pop_mean) / pop_mean) * 100

print(f"mean before training: {pop_mean}")
print(f"mean after training: {mean_after}")
print(f"percentage increase: {round(percentage_increase, 2)}%")
print(f"median: {statistics.mode(df['TransactionAmount'])}")
print(f"modus: {statistics.mode(df['TransactionAmount'])}")
```

    mean before training: 100
    mean after training: 102.6
    percentage increase: 2.6%
    median: 100
    modus: 100



Analisa :
1. Rata-rata setelah pelatihan naik menjadi 102.6, tetapi peningkatan ini sangat kecil (sekitar 2.6% dari rata-rata sebelumnya). Meski tampaknya pelatihan berkontribusi pada peningkatan penjualan, perbedaannya tidak cukup signifikan untuk menarik kesimpulan yang tegas tanpa uji statistik lebih lanjut.
2. Median yang sama dengan nilai rata-rata sebelum pelatihan menunjukkan bahwa distribusi data cukup seimbang di sekitar nilai 100. Ini berarti tidak ada banyak outlier yang menarik rata-rata jauh dari nilai tengah data, yang juga diindikasikan oleh modus (di bawah).
3.Modus yang sama dengan median dan mendekati rata-rata memperkuat indikasi bahwa distribusi data mendekati simetris, tanpa adanya konsentrasi nilai yang terlalu ekstrem.

#### measure of variability


```python
print(f"nilai maximum: {np.max(df['TransactionAmount'])}")
print(f"nilai minimum: {np.min(df['TransactionAmount'])}")
print(f"range: {np.max(df['TransactionAmount']) - np.min(df['TransactionAmount'])}")

print(f"variance: {round(np.var(df['TransactionAmount']),2)}")
print(f"standard deviation: {round(np.std(df['TransactionAmount']),2)}")
print(f"quartile 1: {np.quantile(df['TransactionAmount'], 0.25)}")
print(f"quartile 2: {np.quantile(df['TransactionAmount'], 0.50)}")
print(f"quartile 3: {np.quantile(df['TransactionAmount'], 0.75)}")
```

    nilai maximum: 150
    nilai minimum: 50
    range: 100
    variance: 972.24
    standard deviation: 31.18
    quartile 1: 85.0
    quartile 2: 100.0
    quartile 3: 120.0


Analisa :
1. Range yang besar menunjukkan adanya variasi yang signifikan dalam data penjualan, dari transaksi yang sangat rendah hingga yang sangat tinggi.
2. Standar deviasi yang relatif tinggi (31.18) menunjukkan bahwa penjualan sangat bervariasi. Ini mengindikasikan ketidakkonsistenan dalam performa sales force, meskipun rata-rata adalah $102.6.
3. Data menunjukkan bahwa sebagian besar penjualan berkumpul di sekitar nilai 100, tetapi ada data yang lebih tinggi menuju 150, yang mengindikasikan variabilitas dalam data, seperti yang terlihat dari standar deviasi yang besar.
4. Sebagian besar data (75%) berada di bawah nilai 120, menunjukkan bahwa nilai di atas 120 adalah outlier yang tidak biasa.

### Inferential Statistics

#### Hypothesis Testing


```python
# mengidentifikasi H0 dan H1

# H0 = Penjualan rata-rata setelah training = $100
# H1 = Penjualan rata-rata setelah pelatihan > $100
```


```python
# memilih confidence level sebesar 95%
confiden_level = 95/100

print("confidence level: ", confiden_level)
```

    confidence level:  0.95



```python
# mengidentifikasi alpha (significance level)
alpha = 1 - confiden_level

print(f"alpha: {round(alpha, 2)}")
```

    alpha: 0.05



```python
# mencari nilai test statistics (t-test) dan p-value
t_test, p_value = stats.ttest_1samp(df['TransactionAmount'], pop_mean)
t_round = round(t_test, 2)
p_round = round(p_value, 2)

# menampilkan hasil t-test dan p-value
print(f"t-test: {t_test} to {t_round}")
print(f"p-value: {p_value} to {p_round}")
```

    t-test: 0.4085001556802841 to 0.41
    p-value: 0.6865284813438117 to 0.69



```python
# menentukan degree of freedom
data = len(df['TransactionAmount'])
dof = data - 1
print(f"degree of freedom: {dof}")
```

    degree of freedom: 24



```python
# mencari critical value
critical_value = round(stats.t.ppf(1-alpha, dof), 2)

print(f"critical value: {critical_value}")
```

    critical value: 1.71


#### Kesimpulan

##### membandingkan test statistics (t-test) dengan critical region


```python
print(f"t-test: {t_round}")
print(f"critical value: {critical_value}")
```

    t-test: 0.41
    critical value: 1.71



```python
# berdasarkan aturan yang ada:
# jika tstatistics > critical value (dalam critical region) = menolak H0
# sementara itu, t-statistics < critical value (critical region: 0.41 < 1.71)
# conclusion: gagal menolak H0
```

##### membandingkan p-value dengan significance level (alpha)


```python
print("p-value: ", p_value)
print("significance level (a): ", alpha)
```

    p-value:  0.6865284813438117
    significance level (a):  0.050000000000000044



```python
# Berdasarkan ketentuan yang ada:
# jika p-value <= significance level (alpha), maka H0 ditolak
# sementara itu, p-value > significance level (alpha) ---- Probabilitas mendapatkan hasil yang sama ekstremnya atau lebih ekstrem jika hipotesis nol benar.
# conclusion: gagal menolak H0
```


```python
# mengidentifikasi H0 dan H1

# H0 = Penjualan rata-rata setelah training = $100
# H1 = Penjualan rata-rata setelah pelatihan > $100
```


```python
# kesimpulan uji statistics:
# hasil perbandingan test statistic < critical value, berada di luar critical region.
# hasil perbandingan p-value > alpha.
# gagal menolak H0, yang berarti tidak ada cukup bukti untuk menyatakan bahwa training tersebut meningkatkan penjualan secara signifikan.
```
