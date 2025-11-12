# Makefile for Eagle CAM output (Gerber generation)
# Uses terriblefire78/eagle:v1 Docker container for CAM output

# Variables for CAM output (Gerber generation)
BOARDPREFIX := tfsasi
BOARD := $(BOARDPREFIX).brd
CAMFILE := jlcpcb_4_layer_v9.cam
GITVERSION := $(shell git rev-parse --short HEAD)
DATESTRING := $(shell date +"%Y_%m_%d")
GERBERS := $(BOARDPREFIX)_$(GITVERSION)_$(DATESTRING)
EAGLE_DOCKER := docker run --rm -v $(CURDIR):/work -w /work terriblefire78/eagle:v1 eagle

# Variables for PDF generation
SCH_FILE := $(BOARDPREFIX).sch
PDF_FILE := $(BOARDPREFIX)_$(GITVERSION)_$(DATESTRING).pdf
EAGLE_PDF_DOCKER := docker run --rm -v $(CURDIR):/work -w /work terriblefire78/eagle-pdf

# Default target
.PHONY: all
all: $(GERBERS).zip

# CAM output (Gerber generation) targets
.PHONY: gerbers camfiles
gerbers: $(GERBERS).zip

camfiles: $(GERBERS)

$(GERBERS).zip: $(GERBERS)
	@echo "Creating Gerber archive..."
	zip -r $@ $(GERBERS)/* $(GERBERS)/*/*
	@echo "Gerber archive created: $@"
	-sudo rm -rf $(GERBERS) 2>/dev/null || true

$(GERBERS): $(BOARD) $(CAMFILE)
	@echo "Generating Gerbers for $(BOARD) using $(CAMFILE)..."
	mkdir -p $(GERBERS)
	$(EAGLE_DOCKER) -X -dCAMJOB -j$(CAMFILE) -o$(GERBERS) $(BOARD)
	@echo "Gerbers generated in $(GERBERS)/"

# PDF generation target
.PHONY: pdf
pdf: $(PDF_FILE)

$(PDF_FILE): $(SCH_FILE)
	@echo "Generating PDF schematic from $(SCH_FILE)..."
	$(EAGLE_PDF_DOCKER) $(SCH_FILE) $(PDF_FILE)
	@echo "PDF schematic generated: $(PDF_FILE)"

# Clean generated files
.PHONY: clean
clean: clean-gerbers clean-pdf
	@echo "Cleaned generated files"

.PHONY: clean-pdf
clean-pdf:
	rm -f $(BOARDPREFIX)_*_*.pdf
	@echo "Cleaned PDF files"

.PHONY: clean-gerbers
clean-gerbers:
	-sudo rm -rf $(BOARDPREFIX)_*_*/ 2>/dev/null || rm -rf $(BOARDPREFIX)_*_*/ 2>/dev/null || true
	rm -f $(BOARDPREFIX)_*_*.zip
	@echo "Cleaned Gerber files and directories"

# Clean everything
.PHONY: distclean
distclean: clean clean-gerbers
	@echo "Cleaned all generated files"

# Show help
.PHONY: help
help:
	@echo "Eagle CAM Output Makefile"
	@echo ""
	@echo "Targets:"
	@echo "  all           - Generate Gerber files and create ZIP archive (default)"
	@echo "  gerbers       - Generate Gerber files and create ZIP archive"
	@echo "  camfiles      - Generate Gerber files only (no ZIP)"
	@echo "  pdf           - Generate PDF schematic (no Eagle required)"
	@echo "  clean         - Remove generated PDF and Gerber files"
	@echo "  clean-gerbers - Remove Gerber files and directories"
	@echo "  clean-pdf     - Remove PDF files"
	@echo "  distclean     - Remove all generated files"
	@echo "  help          - Show this help message"
	@echo ""
	@echo "Input:  $(SCH_FILE), $(BOARD)"
	@echo "Output: $(GERBERS).zip, $(PDF_FILE)"
