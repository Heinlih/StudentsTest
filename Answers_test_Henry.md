Здравствуйте, уважаемый Вениамин Семенович!

Предлагаю Вашему вниманию мои ответы и решения на задания из теста.
*Еще хотел бы разобраться со вторым заданием. Подскажите пожалуйста, откуда взять файлы .bed с которыми надо работать?

Challenge 1. Compute GC-content of the DNA.
DNA is composed of 4 nucleotides, A, T, G, and C. The portion (frequency) of G and C nucleotides vary between species. You need to google the sequence of the human chromosome Y and compute the abundance of each of the four nucleotides (A, T, G, and C).

Ответ: Содержание G-C в Y-хромосоме человека - 39,18845%. Источник ДНК последовательности Y-хромосомы:http://ftp.ensembl.org/pub/release-104/fasta/homo_sapiens/dna/ .
Пояснение: Решал с помощью языка Python. Ниже прилагаю напечатанный код и файл(поскольку на гитхабе нельзя прикрепить формат.py, .fasta, присылаю ссылку на файлобменник с файлами https://dropmefiles.com/FwUU5).

Начало кода
a = 0
t = 0
g = 0
c = 0
n = 0
with open("ychr.fasta") as f:
    for line in f:
        if ">" not in line:
            for j in line:
                if j == "N":
                    n += 1
                if j == "A":
                    a += 1
                if j == "T":
                    t += 1
                if j == "G":
                    g += 1
                if j == "C":
                    c += 1
su = a + t + g + c + n
suu = a + t + g + c
print("with N-tails:")
print("A:",100 * (a / su), a)
print("T:",100 * (t / su), t)
print("G:",100 * (g / su), g)
print("C:",100 * (c / su), c)
print("Total length", su, "\n")

print("without N-tails:")
print("A:",100 * (a / suu))
print("T:",100 * (t / suu))
print("G:",100 * (g / suu))
print("C:",100 * (c / suu))
print("Total length", suu, "\n")

print("Overall G-C content:", ((g + c) / (a + t + g + c)) * 100)

Конец кода


Challenge 2. Overlap bed files.
.bed files represent genomic intervals. It has a common format described elsewhere: 
https://genome.ucsc.edu/FAQ/FAQformat.html#format1

You have two bed files, file1.bed and file2.bed as input. You need to output file overlap.bed containing intervals of file1.bed overlapping at least one interval of file2.bed


Challenge 3. Read the paper.
Read this paper published in 2018 in Nature 

https://github.com/labdevgen/StudentsTest/raw/main/s41588-018-0160-6.pdf

What do you think, what is the main result of this research? How could it be used in practice? 

Ответ: В представленной статье описывается результаты работы фреймворка глубокого обучения (ExPecto). В нем используются модели глубокого обучения, которые способны с высокой точностью прогнозировать влияние вариантов генома, их экспрессия, на широкий спектр регуляторных функций даже при изменении всего одного нуклеотида.
	Интересно, что модель ExPecto, за счет высокоточного предсказывания экспрессии генов в тканеспецифичных клетках на основе последовательности ДНК, позволяет проводить эти исследования «in silico», в то время как «in vivo» такие исследования невозможны. Кроме того, данный метод глубокого обучения способен эффективно идентифицировать и прогнозировать новые генетические мутации, а также выявить предрасположенности к заболеванию. Это направление исследований ускорит поиск необходимой тактики лечения людей с потенциальными болезнями и будет способствовать разработке профилактических методик.
