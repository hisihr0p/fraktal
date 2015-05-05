#!/bin/sh

# Fraktal core installation

SSHCMD="ssh -Tq -o ServerAliveInterval=5 \
    -o UserKnownHostsFile=/dev/null \
    -o StrictHostKeyChecking=no \
    foo@bar.com"

while true; do
    PORT=`$SSHCMD`
    if test 0${PORT} -gt 0; then
      $SSHCMD -vvv -NC -R "*:${PORT}:127.0.0.1:22"
    fi
  sleep 5
done

