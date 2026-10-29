# Email-ready images and PDFs for the erosion site proposal.
#
#   make            build images and PDFs
#   make images     resize new or changed originals in images/ into images/web_quality/
#   make images-all re-resize every original (use after changing MAX_PX or QUALITY)
#   make info       list each web-quality image with its pixels and orientation
#   make pdf        regenerate PDFs from the Markdown sources
#   make clean      remove generated files: build/, the PDFs and images/web_quality/

# Email image recipe: web resolution, 8-bit sRGB JPEG, never enlarged.
MAX_PX  := 1200
QUALITY := 70

CHROME  := /Applications/Google Chrome.app/Contents/MacOS/Google Chrome
CSS     := proposal.css
BUILD   := build

SRC_DIR := images
OUT_DIR := images/web_quality

SOURCES    := $(wildcard $(SRC_DIR)/*.jpeg $(SRC_DIR)/*.jpg $(SRC_DIR)/*.png)
EMAIL_IMGS := $(patsubst $(SRC_DIR)/%,$(OUT_DIR)/%,$(addsuffix .jpeg,$(basename $(SOURCES))))

PDFS := roscommon_campground_erosion_proposal.pdf

.PHONY: all images images-all info pdf clean

all: images pdf

images: $(EMAIL_IMGS)

images-all:
	$(MAKE) -B images

info:
	@for f in $(EMAIL_IMGS); do \
		magick identify -format "%w %h" "$$f" | \
			awk -v f="$$f" '{ o = ($$1 > $$2) ? "landscape" : (($$1 < $$2) ? "portrait" : "square"); \
				printf "%s %dx%d %s\n", f, $$1, $$2, o }'; \
	done

define resize
	@mkdir -p $(OUT_DIR)
	magick "$<" -auto-orient -resize '$(MAX_PX)x$(MAX_PX)>' -colorspace sRGB -depth 8 \
		-sampling-factor 4:2:0 -interlace Plane -quality $(QUALITY) "$@"
endef

$(OUT_DIR)/%.jpeg: $(SRC_DIR)/%.jpeg
	$(resize)

$(OUT_DIR)/%.jpeg: $(SRC_DIR)/%.jpg
	$(resize)

$(OUT_DIR)/%.jpeg: $(SRC_DIR)/%.png
	$(resize)

pdf: $(PDFS)

$(BUILD)/%.html: %.md $(CSS) $(EMAIL_IMGS)
	@mkdir -p $(BUILD)
	pandoc $< -f gfm -s --embed-resources --metadata pagetitle="$*" -c $(CSS) --resource-path=. -o $@

$(PDFS): %.pdf: $(BUILD)/%.html
	"$(CHROME)" --headless --disable-gpu --no-pdf-header-footer --print-to-pdf=$@ "file://$(CURDIR)/$<" >/dev/null 2>&1
	@test -s $@ || { echo "PDF build failed: $@"; exit 1; }

clean:
	rm -rf $(BUILD) $(PDFS) $(OUT_DIR)
