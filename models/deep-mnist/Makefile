IMAGE_NAME=127.0.0.1:5000/deep-mnist
MODEL_VERSION=v0

.PHONY: train
train:
	mkdir -p model
	python create_model.py

build_model_image: train
	s2i build . seldonio/seldon-core-s2i-python2 $(IMAGE_NAME):$(MODEL_VERSION)

push_to_registry:
	docker push $(IMAGE_NAME):$(MODEL_VERSION)

.PHONY: clean
clean:
	rm -rf model
	rm -rf MNIST_data

