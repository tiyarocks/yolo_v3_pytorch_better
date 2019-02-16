.PHONY: clean clean-voc detect pascal purge train train-carpk weights

all:
	@echo "make clean - delete yolo_output image folder"
	@echo "make clean-voc - delete all VOC data"
	@echo "make detect - detect an image"
	@echo "make pascal - download and build the Pascal VOC dataset"
	@echo "make train - train on Pascal VOC data"
	@echo "make weights - get YOLO v3 weights"

clean:
	@rm -rf yolo_output/

clean-voc:
	@bash data/pascal_data/clean.sh

detect:
	@python detect.py cfg/yolo_v3.cfg yolov3.weights data/dog-cycle-car.png data/coco.names

pascal:
	@bash data/pascal_data/pascal.sh

purge: clean clean-voc

train:
	@echo 'Update training data pathing in the cfg/*.data files'
	@python train.py -d cfg/voc.data -c cfg/yolo_v3.cfg -w yolov3.weights

train-carpk:
	@echo 'Update training data pathing in the cfg/*.data files'
	@python train.py -d cfg/carpk.data -c cfg/sam.cfg -w yolov3.weights

weights:
	@echo "Getting YOLO v3 weights" && wget https://pjreddie.com/media/files/yolov3.weights yolo_v3/yolov3.weights