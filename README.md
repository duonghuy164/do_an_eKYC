# do_an_eKYC

# Cài đặt các thư viện cần thiết 
pip3 install -r requirements.txt

# Tiền xử lý ảnh 
python3 src/align_dataset_mtcnn.py  Dataset/FaceData/raw Dataset/FaceData/processed --image_size 160 --margin 32  --random_order --gpu_memory_fraction 0.25

# train model 
python3 src/classifier.py TRAIN Dataset/FaceData/processed Models/20180402-114759.pb Models/facemodel.pkl --batch_size 1000

# test với webcam 
python3 src/face_rec_cam.py

# test với video
python3 src/face_rec.py --path video/camtest.mp4 