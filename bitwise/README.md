# Ultralytics

Install this (probably don't need to on google colab)

    conda install numpy opencv matplotlib tqdm pillow
    conda install pytorch torchvision -c pytorch
    conda install -c conda-forge scikit-image

copy all the jpg and txt files from yolov3/bitwise/dataset to ../coco/images/val2014 and ../coco/labels/val2014 respectively, e.g.


!    cp yolov3/bitwise/dataset/*.jpg coco/images/val2014
!    cp yolov3/bitwise/dataset/*.txt coco/labels/val2014

copy all the config files

!   cp yolov3/bitwise/config/* yolov3/data

then actually train stuff

%    cd yolov3
!    python3 train.py --data data/obj.data


Do this if you're stupid and forget to rename the files
!for f in * ; do mv $f bitwise_$f ; done

