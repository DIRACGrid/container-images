FROM ghcr.io/diracgrid/diracx/base

# Copying in ENTRYPOINT script and environment specification
COPY --chown=$MAMBA_USER:$MAMBA_USER environment.yml /tmp/

ENV DIRACX_IMAGE_PACKAGES=core,client,api,cli,.

RUN micromamba install --freeze-installed --yes --file /tmp/environment.yml  --name=base && \
    micromamba clean --all --yes --force-pkgs-dirs && \
    rm -rf /tmp/environment.yml 

# In many clusters the container is ran as a random uid for security reasons.
# If we mark the conda directory as group 0 and give it group write permissions
# then we're still able to manage the environment from inside the container.
USER 0
RUN chown -R $MAMBA_USER:0 /opt/conda && chmod -R g=u /opt/conda
USER $MAMBA_USER
