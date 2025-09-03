---
title: Cấu trúc rời rạc
date: 2025-08-02
tags: 
    - Toán học
    - UMass Lowell
---
- Cấu trúc rời rạc (MATH 2010) Fall 2025 tại UMass Lowell
# Lý thuyết tập hợp

- ## Tập hợp  
  Định nghĩa: tập hợp là một **tập các đối tượng** (gọi là **phần tử**).  
  Ký hiệu: `{ }`

  **Ví dụ**:  
  {{% math %}}
  $$
  S = \{1,2,3,4,5\}
  $$
  {{% /math %}}

  “2 là phần tử của S”:  
  {{% math %}}
  $$
  2 \in S
  $$
  {{% /math %}}

  “7 không là phần tử của S”:  
  {{% math %}}
  $$
  7 \notin S
  $$
  {{% /math %}}

  **Tính chất**:  
  - Tập hợp **không có thứ tự**, tức là:  
    {{% math %}}
    $$
    \{3,2,1\} = \{1,2,3\}
    $$
    {{% /math %}}
  - Các phần tử trong tập hợp là **duy nhất**:  
    {{% math %}}
    $$
    \{4,4\} = \{4\}
    $$
    {{% /math %}}  
    Nhưng thực tế không ai viết tập hợp ở vế phải như vậy.  

  **Ví dụ** (các chữ cái tiếng Anh):  
  {{% math %}}
  $$
  A = \{a, b, c, d, \dots, x, y, z\}
  $$
  {{% /math %}}

---

- ## Các tập hợp thường gặp  

  Tập số nguyên:  
  {{% math %}}
  $$
  \mathbb{Z}
  $$
  {{% /math %}}

  Tập số nguyên dương:  
  {{% math %}}
  $$
  \mathbb{P}
  $$
  {{% /math %}}

  Tập số hữu tỉ: bất kỳ số nào viết được dưới dạng phân số  
  {{% math %}}
  $$
  \mathbb{Q} = \left\{\frac{a}{b} \,\middle|\, a,b \in \mathbb{Z},\; b \neq 0 \right\}
  $$
  {{% /math %}}

  (Dấu gạch đứng “\(|\)” có nghĩa là **“sao cho”**.)

  Tập số thực:  
  {{% math %}}
  $$
  \mathbb{R}
  $$
  {{% /math %}}

  Tập số phức: bao gồm cả số ảo,…  
  {{% math %}}
  $$
  \mathbb{C} = \{\, a + bi \mid a,b \in \mathbb{R},\; i^2 = -1 \,\}
  $$
  {{% /math %}}

  Ta cũng có thể tự tạo tập hợp riêng.  
  **Ví dụ** (tập hữu hạn):  
  {{% math %}}
  $$
  P = \{\text{các con mèo ở Lowell}\}
  $$
  {{% /math %}}

---

- ## Tập con  
  Nói “\(B\) là tập con của \(A\)” nghĩa là mọi phần tử của \(B\) cũng thuộc \(A\):  
  {{% math %}}
  $$
  B \subseteq A \;\Longleftrightarrow\; \forall x\, (x \in B \Rightarrow x \in A)
  $$
  {{% /math %}}

  **Ví dụ**:  
  {{% math %}}
  $$
  S = \{3,4,\{3,4\},7,\{1\}\}
  $$
  {{% /math %}}

  Khi đó:  
  {{% math %}}
  $$
  1 \notin S,\qquad \{1\} \in S,\qquad \{1\} \subseteq S
  $$
  {{% /math %}}

---

> **Một số tính chất**  
> - Mọi tập hợp đều là tập con của chính nó:  
>   {{% math %}}
$$
   A \subseteq A
$$
>   {{% /math %}}
>
> - Hai tập hợp bằng nhau khi và chỉ khi chúng là tập con của nhau:  
>   {{% math %}}
$$
A = B \;\Longleftrightarrow\; (A \subseteq B \;\wedge\; B \subseteq A)
$$
>   {{% /math %}}
