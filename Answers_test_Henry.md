Здравствуйте, уважаемый Вениамин Семенович!

Предлагаю Вашему вниманию мои ответы и решения на задания из теста.

Challenge 1. Compute GC-content of the DNA.
DNA is composed of 4 nucleotides, A, T, G, and C. The portion (frequency) of G and C nucleotides vary between species. You need to google the sequence of the human chromosome Y and compute the abundance of each of the four nucleotides (A, T, G, and C).

Ответ: Содержание G-C в Y-хромосоме человека - 39,18845%. Источник ДНК последовательности Y-хромосомы:http://ftp.ensembl.org/pub/release-104/fasta/homo_sapiens/dna/ .

Пояснение: Решал с помощью языка Python. Ниже прилагаю код и файл(поскольку на гитхабе нельзя прикрепить формат.py, .fasta, присылаю ссылку на файлобменник с файлами https://dropmefiles.com/ZTxaA).

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

Challenge 2. Overlap bed files.
You have two bed files, file1.bed and file2.bed as input. You need to output file overlap.bed containing intervals of file1.bed overlapping at least one interval of file2.bed

Использовал утилиту для работы с .bed файлами - Bedtools.


	sort -k1,1 -k2,2n file1.bed > in.sortedfile1.bed
	sort -k1,1 -k2,2n file2.bed > in.sortedfile2.bed
	bedtools intersect -a in.sortedfile1.bed -b in.sortedfile2.bed -wa > overlap.bed



Challenge 3. Read the paper.
Read this paper published in 2018 in Nature 

https://github.com/labdevgen/StudentsTest/raw/main/s41588-018-0160-6.pdf

What do you think, what is the main result of this research? How could it be used in practice? 

Ответ: В представленной статье описываются результаты работы фреймворка ExPecto, в рамках которого используются модели deep ML для высокоточного прогнозирования влияния изменений в геноме (до одного нуклеотида) и их экспрессии на широкий спектр регуляторных функций. ExPecto используется для предсказания эффектов геномной вариативности на основе последовательностей ДНК пациента, в том числе - для предсказания возникновения различных заболеваний на основе искомых полногеномных данных.

Интересно, что модель ExPecto, за счет высокоточного предсказывания экспрессии генов в тканеспецифичных клетках на основе последовательности ДНК, позволяет проводить подобные исследования «in silico», в то время как «in vivo» такие исследования невозможны. Исследователи показали, что подобное прогнозирование оказалось эффективным для предсказания заболеваний ассоциированных с eQTL и может осуществлено с использования полногеномного сиквенса. Самое интересное, что метод одинаково эффективен как для идентификации распространённых мутаций, так и для редких, что позволяет выйти за пределы возможностей обычной количественной генетики.
Также, получаемые с помощью ExPecto модели экспрессии позволяют предсказывать изменения экспрессии генов человек на основе анализа мутагенеза in silico, который позволяет, например, с очень высокой точностью предсказывать аллель, изменения которого приводят к возникновению HGMD регуляторных мутаций, а также идентифицировать подобные аллели риска GWAS.

Данный метод глубокого обучения способен эффективно идентифицировать и прогнозировать новые генетические мутации, а также выявить предрасположенности к заболеванию. Таким образом, прогнозирование эффектов экспрессии и эволюционных ограничений обеспечивает вычислительную основу для анализа регуляторных мутаций, связанных с различными заболеваниями. Это направление исследований ускорит поиск необходимой тактики лечения людей с потенциальными болезнями и будет способствовать разработке профилактических методик.





