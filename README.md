[![Open in Visual Studio Code](https://classroom.github.com/assets/open-in-vscode-2e0aaae1b6195c2367325f4f02e2d04e9abb55f0b24a779b69b11b9e10269abc.svg)](https://classroom.github.com/online_ide?assignment_repo_id=23574031&assignment_repo_type=AssignmentRepo)
# Day 10 Lab: Data Pipeline & Data Observability

**Student Email:** nguyenhieu6732@gmail.com
**Name:** Nguyễn Văn Hiếu 

---

## Mo ta

Bai lab xay dung mot ETL pipeline don gian tu file JSON sang file CSV co quan sat du lieu.

Trong `solution.py`, pipeline thuc hien cac buoc:
- Extract: doc du lieu tu `raw_data.json`
- Validate: loai bo record khong hop le (price <= 0 hoac category rong)
- Transform: tinh `discounted_price` = 90% gia ban, chuan hoa `category` ve Title Case
- Load: luu ket qua ra `processed_data.csv`
- Observability: in thong tin count record va them cot `processed_at`

Song song do la mot mo phong agent trong `agent_simulation.py` de so sanh ket qua khi dung du lieu "Clean" va "Garbage".

---

## Cach chay (How to Run)

### Prerequisites
```bash
pip install pandas
```

### Chay ETL Pipeline
```bash
python solution.py
```

### Chay Agent Simulation (Stress Test)
```bash
python agent_simulation.py
```

`agent_simulation.py` se thu nghiem voi:
- `processed_data.csv` (Clean Data)
- `garbage_data.csv` (Garbage Data)

---

## Cau truc thu muc

```
├── agent_simulation.py       # Script mo phong agent de test chat data
├── experiment_report.md      # Bao cao thi nghiem
├── garbage_data.csv          # Du lieu rac de test chat bot
├── raw_data.json             # Du lieu goc de pipeline X-ray
├── processed_data.csv        # Ket qua output cua pipeline
├── README.md                 # File nay
└── solution.py               # ETL Pipeline script
```

---

## Ket qua

- `raw_data.json`: 5 records ban dau
- `processed_data.csv`: 3 records hop le duoc giu lai
- 2 record bi loai bo:
  - id 3: `price <= 0`
  - id 4: missing / empty `category`
- `processed_data.csv` da duoc chuan hoa `category` ve Title Case va tinh `discounted_price` = 90% gia ban
- `processed_at` duoc them vao de ghi nhan thoi diem xu ly

**Ghi chu quan sat:**
- Du lieu chat luong giup agent mo phong tra loi dung hon khi dung `processed_data.csv`
- `garbage_data.csv` dung de minh hoa cach du lieu sai lam hoac du lieu bi loi lam giam chat luong cau tra loi
