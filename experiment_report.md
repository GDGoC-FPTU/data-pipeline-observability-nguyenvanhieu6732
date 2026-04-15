# Experiment Report: Data Quality Impact on AI Agent

**Student ID:** 2A202600454
**Name:** Nguyễn Văn Hiếu
**Date:** 15/04/2026

---

## 1. Ket qua thi nghiem

Chay `agent_simulation.py` voi 2 bo du lieu va ghi lai ket qua:

| Scenario | Agent Response | Accuracy (1-10) | Notes |
|----------|----------------|-----------------|-------|
| Clean Data (`processed_data.csv`) | Agent: Based on my data, the best choice is Laptop at $1200. | 9 | Dung du lieu da duoc validated va chuan hoa. |
| Garbage Data (`garbage_data.csv`) | Agent: Based on my data, the best choice is Nuclear Reactor at $999999. | 3 | Du lieu co gia tri bat thuong va du lieu sai lam nen ket qua bi lech. |

---

## 2. Phan tich & nhan xet

### Tai sao Agent tra loi sai khi dung Garbage Data?

Du lieu Garbage Data khien agent mo phong dua ra dap an sai vi co nhieu van de chat luong du lieu:
- Co record duplicated ID (`id=1` xuat hien hai lan), khien tim kiem hoac logic so sanh bi sai.
- Co field `price` dang chuoi `ten dollars` thay vi so, nen model hoac logic xu ly co the bo qua hoac bi crash.
- Co `price` qua lon (`999999`) va `category` dung nham, lam cho tim kiem hoac so sanh theo gia tri co the chon sai muc tieu.
- Co record `price=0` va `category` rong, la du lieu khong hop le nhung van ton tai trong file.

Nhung loi nay lam oto?:
- Agent dua ra san pham co gia tri lon nhat thay vi san pham co y nghia thuc su vi logic tim `best choice` dua tren `category` va `price` ma khong loai bo du lieu sai.
- Du lieu khong duoc validated va chuan hoa se lam cho mo phong phan tich sai, giam do chinh xac chat luong dap an.
- Trong su dung thuc te, khi du lieu rac nhieu hon thi cac he thong RAG/AI se tra ve cau tra loi thieu tin cay hoac khong phu hop voi yeu cau nguoi dung.

Garbage Data cho thay rang: du lieu khong duoc lam sach se anh huong truc tiep den ket qua cua agent, ke ca khi prompt co dung.

---

## 3. Ket luan

**Quality Data > Quality Prompt?**

Dong y. Du lieu chat luong cao la yeu to co ban de agent hoat dong dung. Mot prompt tot cung khong the bu dap duoc su sap xep, validate va chuan hoa du lieu kem chat luong.

Du lieu duoc lam sach va quan sat tot giup:
- Nhan dang duoc y nghia hon
- Giam loi sai khi xay dung cau tra loi
- Tang do tin cay cua he thong

Khi du lieu qua rac, prompt tot nhat cung se tra ve phan hoi sai hoac khong day du.
