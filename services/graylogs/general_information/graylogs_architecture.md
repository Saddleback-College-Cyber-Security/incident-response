# Graylogs Architecture Considerations

[**Graylogs Home**](../README.md)
- [Resources](#Resources)
- [Minimum Setup](#Minimum-Setup)

## Resources

- Graylog nodes should have a focus on CPU power. These also serve the user interface to the browser.
- Elasticsearch nodes should have as much RAM as possible and the fastest disks you can get. Everything depends on I/O speed here.
- MongoDB is storing meta information and configuration data and doesn’t need many resources.

## Minimum Setup

![](https://docs.graylog.org/en/3.2/_images/architec_small_setup.png)