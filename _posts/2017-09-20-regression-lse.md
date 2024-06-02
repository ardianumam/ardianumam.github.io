---
layout: post
title: Linear Regression Using Least Square Estimation
date: 2017-09-20 11:12:00-0400
description: 
tags: machine-learning regression lse
categories: machine-learning
disqus_comments: true
comments: true
related_posts: true
---


<strong><a name="bahasa"></a>Language : <a href="#english">[English]</a><a href="#bahasa">[Bahasa Indonesia]</a></strong>

Mempelajari <em>linear regression</em> adalah langkah yang baik untuk mengawali mempelajari <em>machine learning, </em>karena sederhana dan dapat memberikan intuisi bagaimana <em>machine </em>belajar dari suatu data. Lihat gambar di bawah ini.

<a href="https://ardianumam.files.wordpress.com/2017/09/regression-linear.png"><img class="aligncenter wp-image-120" src="https://ardianumam.files.wordpress.com/2017/09/regression-linear.png" alt="" width="246" height="197" /></a>

Diberikan sejumlah data <span style="color: #ff0000;">(titik-titik warna merah), <span style="color: #000000;">dan kita ingin mendapatkan suatu fungsi garis <span style="color: #0000ff;">(garis biru)</span> yang paling sesuai untuk merepresentasikan data titik-titik tersebut. Dalam konteks <em>machine learning, </em>kita akan menggunakan data titik-titik tersebut sebagai data training untuk membuat suatu fungsi linear yang paling sesuai untuk merepresentasikan data tersebut. Gambar di atas memiliki input satu komponen nilai (satu titik) dengan output satu komponen nilai juga. Dalam case ini, kita akan menggeneralisasinya menggunakan <em>1-dimensional</em> array (vektor) dengan $$n$$ komponen untuk inputnya, dengan output 1 komponen nilai. Kita dapat menuliskan model persamaan <em>linear regression</em> kita sebagai berikut, dengan $$ h(\mathbf{x})$$ adalah <em>hypothesis/prediction</em> untuk input $$ \mathbf{x}$$.

$$h(\mathbf{x})=a_0x_0+a_1x_1+a_2x_2+....+a_nx_n$$

Mungkin ada yang bertanya, kenapa linear modelnya bukan $$ h(x)=ax+b$$ ? Untuk bentuk tersebut saya bahas sekalian dengan bentuk polinomial <a href="https://ardianumam.wordpress.com/2017/09/21/polynomial-regression-using-least-square-estimation">di sini</a>, yakni dengan mensetting orde $$ n=1$$.

Kembali lagi, kita dapat menuliskan persamaan di atas menggunakan notasi matrik sebagai berikut.

$$ h(\mathbf{x})=\mathbf{a}^{T}\mathbf{x} \text{ dengan } \mathbf{a}=\begin{bmatrix} a_0\\a_1\\a_2\\... \\a_n\end{bmatrix} \text{ dan } \mathbf{x}=\begin{bmatrix} x_0\\x_1\\x_2\\... \\x_n\end{bmatrix}$$

Kemudian kita dapat menuliskan untuk $$ m $$ pasang input-output prediksi dalam notasi matrik sebagai berikut.

$$ \begin{bmatrix} h(x_1)\\h(x_2)\\h(x_3)\\... \\h(x_m)\end{bmatrix}= \begin{bmatrix} x_{10}\,\,x_{11}\,\,x_{12}\,... \,x_{1n}\\x_{20}\,\,x_{21}\,\,x_{22}\,... \,x_{2n}\\x_{30}\,\,x_{31}\,\,x_{32}\,... \,x_{3n}\\... \,\,... \,\,... \,... \\x_{m0}\,\,x_{m1}\,\,x_{m2}\,... \,x_{mn}\end{bmatrix}\begin{bmatrix} a_0\\a_1\\a_2\\... \\a_n\end{bmatrix} $$

$$ h(\mathbf{x})=\mathbf{Xa} $$

Dalam <em>case</em> ini, <em>"design matrix" </em>kita adalah $$ \begin{bmatrix} x_{10}\,\,x_{11}\,\,x_{12}\,... \,x_{1n}\\x_{20}\,\,x_{21}\,\,x_{22}\,... \,x_{2n}\\x_{30}\,\,x_{31}\,\,x_{32}\,... \,x_{3n}\\... \,\,... \,\,... \,... \\x_{m0}\,\,x_{m1}\,\,x_{m2}\,... \,x_{mn}\end{bmatrix}$$, dan kita menyimbolkannya dengan $$ \mathbf{X}$$.

Pertanyaan selanjutnya, bagaimana cara mengukur seberapa baik fungsi <em>linear regression </em>kita? Kita dapat membuat <em>cost function, $$ J(\mathbf{a}) $$, </em>untuk mengukur seberapa besar eror dari fungsi <em>linear regression </em>kita. Pada case ini, kita akan menggunakan <i>average of square error</i> (rerata eror kuadrat)<i> </i> untuk <em>cost function</em> kita. Dan tujuan kita adalah meminimalkan nilai eror tersebut. Oleh karena itu, metode ini disebut dengan <em>least square estimation</em>.

$$ J(\mathbf{a}) =\frac{1}{2m}\sum_{i=1}^{m}(h(x_i)-y_i)^{2}$$

Konstanta $$ \frac{1}{2}$$ pada persamaan di atas biasanya ditambahkan karena itu dapat menghilangkan konstanta $$ 2 $$ dari operasi kuadrat ketika kita menurunkan persamaan tersebut ke turunan pertama. Tetapi untuk kasus kita kali ini, konstanta $$ \frac{1}{2m}$$ akan hilang, karena kita akan membandingkan turunan pertama dari persamaan tersebut sama dengan nol. Kembali ke kasus kita, selanjutnya kita akan mensubtitusikan persamaan $$ h(\mathbf{x}) $$  ke  $$ J(\mathbf{a}) $$, dan menyederhanakannya sebagai berikut.

$$ J(\mathbf{a}) =\frac{1}{2m}(\mathbf{Xa}-\mathbf{y})^{2}=\frac{1}{2m}(\mathbf{Xa}-\mathbf{y})^T(\mathbf{Xa}-\mathbf{y})$$

$$ J(\mathbf{a}) =\frac{1}{2m}((\mathbf{Xa})^T-\mathbf{y}^T)(\mathbf{Xa}-\mathbf{y})$$

$$ J(\mathbf{a})=\frac{1}{2m}((\mathbf{Xa})^T\mathbf{Xa}-(\mathbf{Xa})^T\mathbf{y}-\mathbf{y}^T\mathbf{Xa}+\mathbf{y}^T\mathbf{y})$$

Simak perlahan persamaan di atas, setiap suku persamaan di atas akan menghasilkan nilai skalar. Sebagai contohnya suku ke-4 sebagai berikut:

$$ \mathbf{y}^T\mathbf{y}=\begin{bmatrix} y_0\,y_1\,y_2\,... \,y_n\end{bmatrix}\begin{bmatrix} y_0\\y_1\\y_2\\... \\y_n\end{bmatrix}=y_0^2+y_1^2+y_2^2+... +y_n^2=\text{nilai skalar}$$

Sehingga, kita dapat mengubah suku ketiga, $$ \mathbf{y}^T(\mathbf{Xa})=(\mathbf{Xa})^T\mathbf{y}$$  dikarenakan keduanya akan menghasilkan nilai skalar yang sama (perkalian bersifat komutatif). Kemudian, dengan mengkombinasikan suku kedua dan ketiga, kita dapat menyederhanakan persamaan $$ J(\mathbf{a})$$ menjadi:

$$ J(\mathbf{a})=\frac{1}{2m}((\mathbf{Xa})^T\mathbf{Xa}-2\mathbf{Xa}^T\mathbf{y}+\mathbf{y}^T\mathbf{y})$$

Tujuan kita dalam <em>linear regression </em>ini sekali lagi adalah untuk mencari fungsi linear yang memiliki nilai eror, $$ J(\mathbf{a})$$, seminimal mungkin. Dan dalam kasus ini, kita akan mencari parameter $$ \mathbf{a}$$ yang memiliki nilai eror, $$ J(\mathbf{a})$$, paling kecil. Untuk melakukannya, kita sudah tahu dari pelajaran matematika saat SMA atau mata kuliah kalkulus di universitas yang mana dengan menghitung turunan pertama terhadap $$ \mathbf{a} $$, kemudian di-sama-dengankan nol. Berikut ini adalah prosesnya.

$$ \frac{dJ(\mathbf{a})}{d\mathbf{a}}=\frac{1}{2m}(2\mathbf{X}^T\mathbf{Xa}-2\mathbf{X}^T\mathbf{y})=0$$

$$ (\mathbf{X}^T\mathbf{Xa}-\mathbf{X}^T\mathbf{y})=0$$

$$ \mathbf{X}^T\mathbf{Xa}=\mathbf{X}^T\mathbf{y}$$

$$ \mathbf{a}=(\mathbf{X}^T\mathbf{X})^{-1}\mathbf{X}^T\mathbf{y}$$

<em><strong>Selamat!</strong> </em>Kita telah menemukan nilai parameter $$ \mathbf{a} $$ untuk fungsi <em>linear regression </em>kita yang paling bagus (paling kecil erornya), dengan catatan matrik $$ (\mathbf{X}^T\mathbf{X})$$ bisa diinverskan (<em>inversible</em>). Dengan menuliskan ulang model <em>linear regression </em>kita, fungsi <em>hypothesis</em> kita menjadi:

$$ h(\mathbf{x})=a_0x_0+a_1x_1+a_2x_2+....+a_nx_n$$

$$\text{dengan }\mathbf{a}=(\mathbf{X}^T\mathbf{X})^{-1}\mathbf{X}^T\mathbf{y}\text{, di mana }\mathbf{X}=\begin{bmatrix}x_{10}\,\,x_{11}\,\,x_{12}\,... \,x_{1n}\\x_{20}\,\,x_{21}\,\,x_{22}\,... \,x_{2n}\\x_{30}\,\,x_{31}\,\,x_{32}\,... \,x_{3n}\\... \,\,... \,\,... \,... \\x_{m0}\,\,x_{m1}\,\,x_{m2}\,... \,x_{mn}\end{bmatrix}$$
 

<br>
<hr/>
<strong><a name="english"></a>Language : <a href="#english">[English]</a><a href="#bahasa">[Bahasa Indonesia]</a></strong>
<h2>Linear Regression using Least Square Estimation</h2>
It is a good start to learn regression linear on machine learning study, since it is simple and can give intuitive meaning how a machine learns a bunch of data. See picture below.

<a href="https://ardianumam.files.wordpress.com/2017/09/regression-linear.png"><img class="aligncenter wp-image-120" src="https://ardianumam.files.wordpress.com/2017/09/regression-linear.png" alt="" width="246" height="197" /></a>

Given data points <span style="color: #ff0000;">(red dots)</span> and we want to plot a linear line that fits those data <span style="color: #0000ff;">(blue line)</span>. In machine learning context, we will use those data points as training data to make best linear function to fit those those points. Picture above has one input element with one output element. We will use 1-dimensional array with $$ n $$ component for input with one output element. Our linear model can be written as follow, with $$ h(\mathbf{x})$$ means <em>hypothesis/prediction</em> of input $$ \mathbf{x}$$.

$$ h(\mathbf{x})=a_0x_0+a_1x_1+a_2x_2+....+a_nx_n$$

Maybe someone will ask, "<em>why do our linear model is not</em>  $$ h(x)=ax+b$$ <em>?</em>" For that model, I discuss it in general polynomial model <a href="https://ardianumam.wordpress.com/2017/09/21/polynomial-regression-using-least-square-estimation">here</a>, by setting order $$ n=1$$.

Back to our case, we can represent equation above using matrix notation.

$$ h(\mathbf{x})=\mathbf{a}^{T}\mathbf{x} $$  with  $$ \mathbf{a}=\begin{bmatrix} a_0\\a_1\\a_2\\... \\a_n\end{bmatrix}$$  and  $$ \mathbf{x}=\begin{bmatrix} x_0\\x_1\\x_2\\... \\x_n\end{bmatrix}$$

Then, we can write equation above in another matrix form with $$ m $$ pair input-output prediction.

$$ \begin{bmatrix} h(x_1)\\h(x_2)\\h(x_3)\\... \\h(x_m)\end{bmatrix}= \begin{bmatrix} x_{10}\,\,x_{11}\,\,x_{12}\,... \,x_{1n}\\x_{20}\,\,x_{21}\,\,x_{22}\,... \,x_{2n}\\x_{30}\,\,x_{31}\,\,x_{32}\,... \,x_{3n}\\... \,\,... \,\,... \,... \\x_{m0}\,\,x_{m1}\,\,x_{m2}\,... \,x_{mn}\end{bmatrix}\begin{bmatrix} a_0\\a_1\\a_2\\... \\a_n\end{bmatrix} $$

$$ h(\mathbf{x})=\mathbf{Xa} $$

In this case,  our <em>"design matrix" </em>is $$ \begin{bmatrix} x_{10}\,\,x_{11}\,\,x_{12}\,... \,x_{1n}\\x_{20}\,\,x_{21}\,\,x_{22}\,... \,x_{2n}\\x_{30}\,\,x_{31}\,\,x_{32}\,... \,x_{3n}\\... \,\,... \,\,... \,... \\x_{m0}\,\,x_{m1}\,\,x_{m2}\,... \,x_{mn}\end{bmatrix}$$, and we denote it using $$ \mathbf{X}$$.

The next question is, "<em>how can we measure how good our linear function toward those data points?"</em> We can define an error <em>cost function,</em> $$ J(\mathbf{a}) $$, and we will use <em>average of square error</em> as our basic form. Our purpose is to minimize the error as small as we can. That's why we call this method <em>least square estimation</em>.

$$ J(\mathbf{a}) =\frac{1}{2m}\sum_{i=1}^{m}(h(x_i)-y_i)^{2}$$

Constant $$ \frac{1}{2}$$ in equation above is usually put because it can cancel constant $$ 2 $$ out from <em>square </em>operation when we take first differential. But it our case, constant $$ \frac{1}{2m}$$ will be thrown since later, we will compare the first differential of the equation with zero. Back to our case, we proceed to put $$ h(\mathbf{x}) $$  to  $$ J(\mathbf{a}) $$ following by doing some linear algebras to simplify it. Here we go.

$$ J(\mathbf{a}) =\frac{1}{2m}(\mathbf{Xa}-\mathbf{y})^{2}=\frac{1}{2m}(\mathbf{Xa}-\mathbf{y})^T(\mathbf{Xa}-\mathbf{y})$$

$$ J(\mathbf{a}) =\frac{1}{2m}((\mathbf{Xa})^T-\mathbf{y}^T)(\mathbf{Xa}-\mathbf{y})$$

$$ J(\mathbf{a})=\frac{1}{2m}((\mathbf{Xa})^T\mathbf{Xa}-(\mathbf{Xa})^T\mathbf{y}-\mathbf{y}^T\mathbf{Xa}+\mathbf{y}^T\mathbf{y})$$

Look carefully to the equation above, each term above will produce scalar value, for example:

$$ \mathbf{y}^T\mathbf{y}=\begin{bmatrix} y_0\,y_1\,y_2\,... \,y_n\end{bmatrix}\begin{bmatrix} y_0\\y_1\\y_2\\... \\y_n\end{bmatrix}=y_0^2+y_1^2+y_2^2+...+y_n^2=scalar\,value$$

Thus, we can change third term, $$ \mathbf{y}^T(\mathbf{Xa})=(\mathbf{Xa})^T\mathbf{y}$$  since these will produce same scalar value (multiplication is commutative). Then, by combining second and third term, we can simplify $$ J(\mathbf{a})$$ become:

$$ J(\mathbf{a})=\frac{1}{2m}((\mathbf{Xa})^T\mathbf{Xa}-2\mathbf{Xa}^T\mathbf{y}+\mathbf{y}^T\mathbf{y})$$

Our purpose for linear regression is to find a linear function that gives minimal error value, $$ J(\mathbf{a})$$. And in our case, we will find parameter $$ \mathbf{a}$$ that gives minimal value of $$ J(\mathbf{a})$$. To do so, we already know in high school math or in undergraduate calculus course that we can take first differential toward $$ \mathbf{a} $$, and make it equal to zero. Here we go.

$$ \frac{dJ(\mathbf{a})}{d\mathbf{a}}=\frac{1}{2m}(2\mathbf{X}^T\mathbf{Xa}-2\mathbf{X}^T\mathbf{y})=0$$

$$ (\mathbf{X}^T\mathbf{Xa}-\mathbf{X}^T\mathbf{y})=0$$

$$ \mathbf{X}^T\mathbf{Xa}=\mathbf{X}^T\mathbf{y}$$

$$ \mathbf{a}=(\mathbf{X}^T\mathbf{X})^{-1}\mathbf{X}^T\mathbf{y}$$

<em><strong>Voila!</strong></em> We can get the value of $$ \mathbf{a} $$ for our linear function that best fits our data points, assuming that  $$ (\mathbf{X}^T\mathbf{X})$$ is invertible. Thus, re-plugging in to our linear model, our <em>hypothesis</em> function become:

$$ h(\mathbf{x})=a_0x_0+a_1x_1+a_2x_2+....+a_nx_n$$

$$\text{with }\mathbf{a}=(\mathbf{X}^T\mathbf{X})^{-1}\mathbf{X}^T\mathbf{y} \text{, where }\mathbf{X}=\begin{bmatrix} x_{10}\,\,x_{11}\,\,x_{12}\,... \,x_{1n}\\x_{20}\,\,x_{21}\,\,x_{22}\,... \,x_{2n}\\x_{30}\,\,x_{31}\,\,x_{32}\,... \,x_{3n}\\... \,\,... \,\,... \,... \\x_{m0}\,\,x_{m1}\,\,x_{m2}\,... \,x_{mn}\end{bmatrix}$$