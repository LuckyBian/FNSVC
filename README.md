# FNSVC

#Data Pre-precessing:
put all raw data into raw data folder, and change the route in the python files
python prepare_data.py

# Get PPGs features
source ./pypath.sh
bash bin/audio_prepare.sh ./data/cut_data scp/
python3 bin/make_ppg.py scp/wav.scp ./features/ppg

# Train FNSVC model
python train.py

# Train Resnet model
python resnet/train.py

# Train HiFiGAN model
python hifigan/train.py

# Eval
python eval.py

# Get the Output
change the route
python inference_e2e.py
