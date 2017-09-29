VER=6.0

help:
	@echo "targets:"
	@echo "  checkout: remove directory unifield then fetch the code into it"
	@echo "  build: build the Docker images, store them locally"
	@echo "  push: push the Docker images to Docker Hub"
	@echo
	@echo "Add the VER=xxx to the end to checkout tag xxx"
	@echo "from Bazaar, i.e. make build VER=2.1-3"

# Print a help message if the bzr setup is not as expected.
check_bzr:
	@[ ! -d $(HOME)/unifield/server/branches ] && echo "Follow the instructions here to set up bzr as expected:" && echo "  https://wiki.unifield.org/doku.php?id=development:tools:bazaar#working_with_multiple_branches" && exit 1 || exit 0
	cd $(HOME)/unifield/server/branches/trunk && bzr pull
	cd $(HOME)/unifield/web/branches/trunk && bzr pull

checkout: check_bzr
	rm -r unifield
	mkdir -p unifield
	bzr checkout --lightweight -r uf$(VER) $(HOME)/unifield/server/branches/trunk unifield/server
	bzr checkout --lightweight -r uf$(VER) $(HOME)/unifield/web/branches/trunk unifield/web

build:
	docker build -f Dockerfile-web -t unifield/web:$(VER) .
	docker build -f Dockerfile-server -t unifield/server:$(VER) .

push:
	docker push unifield/web:$(VER)
	docker push unifield/server:$(VER)
