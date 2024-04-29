all: html latex

latex:
	jupyter-book build . --builder pdflatex

html:
	mkdir -p _build/.jupyter_cache
	jupyter-book build .
	ghp-import -n -p -f _build/html

clean:
	# keep jupyter-cache cache folder
	jupyter-book clean .

full-clean:
	rm -rf _build
