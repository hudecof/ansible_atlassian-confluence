CrowdSSO Integration
====================

Interation of the CrowdSSO is baed on Atlassian documenation

- https://confluence.atlassian.com/display/CROWD/The+crowd.properties+file
- https://confluence.atlassian.com/display/CROWD/Integrating+Crowd+with+Atlassian+Confluence

crowd.properties
----------------

Configuration file is moves to `atlassian_confluence_home` directory. The **CATALINA_OPTS** in `bin/setenv.sh` are changed to reflect it.

If this file exists is not overwritten, so you can write there your own configuration items. See the variables section which variabes could be manageged.

Variables
---------

`atlassian_confluence_crowd` must be set to `true` to enable the CrowsSSO.

`atlassian_confluence_crowd_url` is default set to `http://localhost:8095/crowd`. This is uses to set following properties

- application.login.url
- crowd.server.url
- crowd.base.url 

To manage other properties use `atlassian_confluence_crowd_properties` this way

    atlassian_confluence_crowd_properties:
      - name: PROPERTY NAME
        value: PROPERTY VALUE


I do not manage the `application.name` and `application.password` for security reason. Sst it maunally for the first timei or use `atlassian_confluence_crowd_properties`.

`atlassian_confluence_seraph_config` is to change the **seraph_config.xml**. The `/security-config/authenticator` is changed automaticly, do not add it here. The config could look like

    atlassian_confluence_seraph_config:
      - xpath: XPATH
      - value: VALUE
      - attribite: default is OMIT
      - ensure: default is present


    atlassian_confluence_seraph_config:
      - xpath: /security-config/parameters/init-param[param-name='link.login.url']/param-value
        value: YOUR COMPANY SSO LOGIN LINK

