# SOFE4630U-highdtrafficanalysis
We used the HighD dataset from the https://www.highd-dataset.com/ and the format of the parameteres we wanted using https://www.highd-dataset.com/format.
Using the https://www.highd-dataset.com/format, we found out that the necessary data we need are called 'data/*recordingMeta.csv'.
The datasets were dowloaded using the google drive link given to us "https://drive.google.com/file/d/11gCCExNIA0S0suhfiwWOjHGCwr9KogQ7/view?usp=share_link".
First created a storage bucket and by using the below commands in the google console, we extracted the datasets we needed into the bucket.
### To download the dataset:
wget --load-cookies /tmp/cookies.txt "https://docs.google.com/uc?export=download&confirm=$(wget --quiet --save-cookies /tmp/cookies.txt --keep-session-cookies --no-check-certificate 'https://docs.google.com/uc?export=download&id=11gCCExNIA0S0suhfiwWOjHGCwr9KogQ7' -O- | sed -rn 's/.*confirm=([0-9A-Za-z_]+).*/\1\n/p')&id=11gCCExNIA0S0suhfiwWOjHGCwr9KogQ7" -O highd-dataset-v1.0.zip && rm -rf /tmp/cookies.txt | gsutil cp - gs://cchighdtraffic/highd-dataset-v1.0.zip
### To send the dataset to the bucket:
gsutil cp gs://cchighdtraffic/highd-dataset-v1.0.zip .
### To get the data we needed:
unzip highd-dataset-v1.0.zip 'data/*recordingMeta.csv'
### To send the data we needed to the bucket:
gsutil cp data/*recordingMeta.csv gs://cchighdtraffic/
