## Deploy ml Model to detect credit card fraud detection with Bentoml

```bash
git clone https://github.com/Vaibhav-Ahuja1/bentoml.git
``` 
```bash 
cd bentoml_ccfd 
``` 
```bash
pip install -r requirements.txt
```
```bash
python3 train.py 
```
```bash
bentoml serve service.py:svc --reload
```
#### replace <instance_public_ip>  with your <machine_public_ip> example: https://54.164.180.20:3000/

#### https://<instance_public_ip>:3000/

