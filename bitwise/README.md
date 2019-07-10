# Ultralytics

Install this (probably don't need to on google colab)

    conda install numpy opencv matplotlib tqdm pillow
    conda install pytorch torchvision -c pytorch
    conda install -c conda-forge scikit-image

copy all the jpg and txt files from yolov3/bitwise/dataset to ../coco/images/val2014 and ../coco/labels/val2014 respectively, e.g.

    cd yolov3/bitwise/dataset
    cp *.jpg ../coco/images/val2014
    cp *.txt ../coco/labels/val2014
    cd ../../

run the following command

    python3 train.py --data data/obj.data
