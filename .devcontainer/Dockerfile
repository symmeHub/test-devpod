FROM mcr.microsoft.com/devcontainers/base:jammy


ARG CONDA_ENV_NAME=record
ENV CONDA_ENV_NAME=${CONDA_ENV_NAME}
ENV CONDA_ENV_BIN_PATH=/opt/conda/envs/${CONDA_ENV_NAME}/bin

COPY _install_apt_package.sh /tmp/_install_apt_package.sh
RUN /tmp/_install_apt_package.sh


COPY _install_miniforge.sh /tmp/_install_miniforge.sh
RUN /tmp/_install_miniforge.sh

COPY environment.yml /tmp/environment.yml
RUN /opt/conda/condabin/mamba env update --name ${CONDA_ENV_NAME} --file /tmp/environment.yml --prune

RUN echo ". /opt/conda/etc/profile.d/conda.sh" >> /home/vscode/.bashrc
RUN echo "conda activate $CONDA_ENV_NAME" >> /home/vscode/.bashrc
