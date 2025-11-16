
FROM nvcr.io/nvidia/tritonserver:25.10-py3


ENV LC_ALL=C.UTF-8

# exclude pip from -U , otherwise: ERROR: Cannot uninstall pip 24.0, RECORD file not found. Hint: The package was installed by debian.
# RUN python3 -m pip install --no-cache-dir -U pip 

# install base package
RUN python3 -m pip install --no-cache-dir -U clearml-serving

# get latest execution code from the git repository
# RUN cd $HOME && git clone https://github.com/allegroai/clearml-serving.git
COPY clearml_serving /root/clearml/clearml_serving

RUN python3 -m pip install --no-cache-dir -r /root/clearml/clearml_serving/engines/triton/requirements.txt

# default serving port
EXPOSE 8001

# environement variable to load Task from CLEARML_SERVING_TASK_ID, CLEARML_SERVING_PORT

WORKDIR /root/clearml/
ENTRYPOINT ["clearml_serving/engines/triton/entrypoint.sh"]
