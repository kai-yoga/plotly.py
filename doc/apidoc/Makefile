# Minimal makefile for Sphinx documentation
#

# You can set these variables from the command line.
SPHINXOPTS    =
SPHINXBUILD   = python -m sphinx
SOURCEDIR     = .
BUILDDIR      = _build

# Put it first so that "make" without argument is like "make help".
help:
	@$(SPHINXBUILD) -M help "$(SOURCEDIR)" "$(BUILDDIR)" $(SPHINXOPTS) $(O)

.PHONY: help Makefile

# Catch-all target: route all unknown targets to Sphinx using the new
# "make mode" option.  $(O) is meant as a shortcut for $(SPHINXOPTS).
# For sphinx-apidoc the first positional path is the module to document
# then all the other ones are paths to exclude for the doc generation
%: Makefile
	sed -i 's/:class:`plotly.graph_objects/:class:`plotly.graph_objs/g' ../../packages/python/plotly/plotly/graph_objs/*.py
	sed -i 's/:class:`plotly.graph_objects/:class:`plotly.graph_objs/g' ../../packages/python/plotly/plotly/graph_objs/*/*.py
	sed -i 's/:class:`plotly.graph_objects/:class:`plotly.graph_objs/g' ../../packages/python/plotly/plotly/graph_objs/*/*/*.py
	sed -i 's/:class:`plotly.graph_objects/:class:`plotly.graph_objs/g' ../../packages/python/plotly/plotly/graph_objs/*/*/*/*.py
	cp ../../packages/python/plotly/_plotly_utils/colors/sequential.py ../../packages/python/plotly/_plotly_utils/colors/diverging.py ../../packages/python/plotly/_plotly_utils/colors/qualitative.py ../../packages/python/plotly/_plotly_utils/colors/cyclical.py ../../packages/python/plotly/plotly/colors
	cp ../../packages/python/plotly/_plotly_utils/colors/sequential.py ../../packages/python/plotly/_plotly_utils/colors/diverging.py ../../packages/python/plotly/_plotly_utils/colors/qualitative.py ../../packages/python/plotly/_plotly_utils/colors/cyclical.py ../../packages/python/plotly/plotly/express/colors
	sphinx-apidoc -M -o generated ../../packages/python/plotly/plotly ../../packages/python/plotly/plotly/validators ../../packages/python/plotly/plotly/tests ../../packages/python/plotly/plotly/matplotlylib/ ../../packages/python/plotly/plotly/offline ../../packages/python/plotly/plotly/api
	@$(SPHINXBUILD) -M $@ "$(SOURCEDIR)" "$(BUILDDIR)" $(SPHINXOPTS) $(O)
	git checkout -- ../../packages/python/plotly/plotly/graph_objs
	rm ../../packages/python/plotly/plotly/colors/diverging.py ../../packages/python/plotly/plotly/colors/sequential.py ../../packages/python/plotly/plotly/colors/qualitative.py ../../packages/python/plotly/plotly/colors/cyclical.py
	rm ../../packages/python/plotly/plotly/express/colors/diverging.py ../../packages/python/plotly/plotly/express/colors/sequential.py ../../packages/python/plotly/plotly/express/colors/qualitative.py ../../packages/python/plotly/plotly/express/colors/cyclical.py
	rename 's/graph_objs/graph_objects/' _build/html/*.html _build/html/generated/*.html
	mv _build/html/generated/plotly.graph_objs.html _build/html/generated/plotly.graph_objects.html
	sed -i 's/graph_objs/graph_objects/g' _build/html/*.html 
	sed -i 's/graph_objs/graph_objects/g' _build/html/*.inv 
	sed -i 's/graph_objs/graph_objects/g' _build/html/*.js 
	sed -i 's/graph_objs/graph_objects/g' _build/html/generated/*.html 
	sed -i 's/graph_objs/graph_objects/g' _build/html/generated/generated/*.html
