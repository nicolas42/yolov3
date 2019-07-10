# Ultralytics

Installation - not needed on colab

    conda install numpy opencv matplotlib tqdm pillow
    conda install pytorch torchvision -c pytorch
    conda install -c conda-forge scikit-image

Edit > Notebook Settings > select GPU (also increases storage to ~350gb for some reason)

    !git clone https://github.com/nicolas42/yolov3
    !bash yolov3/data/get_coco_dataset.sh

copy all the jpg and txt files from yolov3/bitwise/dataset to ../coco/images/val2014 and ../coco/labels/val2014 respectively, e.g.


!    cp yolov3/bitwise/dataset/*.jpg coco/images/val2014
!    cp yolov3/bitwise/dataset/*.txt coco/labels/val2014
!    cp yolov3/bitwise/config/* yolov3/data

then actually train stuff

%    cd yolov3
#!    git pull
!    python3 train.py --data data/obj.data


(Do this if you're stupid and forget to rename the files
!for f in * ; do mv $f bitwise_$f ; done)

Upload Results to Dropbox
You'll need to follow the instructions to get an authentication key if you don't already have one.

    !git clone https://github.com/andreafabrizi/Dropbox-Uploader.git
    %cd Dropbox-Uploader/
    !chmod +x dropbox_uploader.sh
    !./dropbox_uploader.sh
    <need dropbox authentication key>
    ./dropbox_uploader.sh upload src dest


Training settings
These are the settings of the previous train. It seems that yolov3-spp.cfg and epochs=100 are set by default.

Namespace(accumulate=8, batch_size=8, bucket='', cfg='cfg/yolov3-spp.cfg', data_cfg='data/obj.data', epochs=100, evolve=False, img_size=416, nosave=False, notest=False, num_workers=4, rect=False, resume=False, single_scale=False, transfer=False, var=0, xywh=False)
Using CUDA device0 _CudaDeviceProperties(name='Tesla T4', total_memory=15079MB)



# Test darknet
!git clone https://github.com/nicolas42/nick-darknet.git
%cd nick-darknet
!make
%cd bitwise
!wget https://pjreddie.com/media/files/darknet53.conv.74
#wget https://pjreddie.com/media/files/darknet19_448.conv.23
#wget https://www.dropbox.com/s/yvca2um3dketvxi/first-test-core-yolo-obj_20000.weights?dl=0
#!git pull
#!cat Makefile
%cd ../

%%capture
!./darknet detector train bitwise/obj.data bitwise/yolov3.cfg bitwise/darknet53.conv.74

Edit a file in Colab

    p = """
    Yadda yadda
    whatever you want just don't use triple quotes.
    """

    c = """text_file = open("text.text", "w+");text_file.write(p);text_file.close()""" 

    exec(c)


