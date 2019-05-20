# Pull base image
# ---------------
FROM oracle11gxe

# Environment variables required for this build (do NOT change)
# -------------------------------------------------------------
ENV INSTALL_FILE_1="apex_18.2.zip" \
    INSTALL_DIR="$HOME/install" \
	RUN_FILE="runOracle1.sh" 

COPY $INSTALL_FILE_1 $RUN_FILE $INSTALL_DIR/

RUN cd $INSTALL_DIR && \	
    unzip $INSTALL_FILE_1 && \
	chmod 6751 $ORACLE_HOME/bin/*
	
RUN $INSTALL_DIR/$RUN_FILE

RUN echo "Installing APEX." && \
	su -p oracle -c "cd /install/apex && sqlplus -s / as sysdba @apexins APEX APEX TEMP /i/ " && \
	su -p oracle -c "cd /install/apex && sqlplus -s / as sysdba @apex_epg_config.sql /install" 
	