---
title: Java Tech Stack
parent: System Design
nav_order: 99
---

# Java Tech Stack
{: .no_toc }


<style type="text/css">
    .ritz .waffle a {
    color: inherit;
    }
    .ritz .waffle .s0 {
    background-color: #ffffff;
    text-align: left;
    color: hsl(0, 0%, 100%);
    font-family: Arial;
    font-size: 12pt;
    vertical-align: top;
    white-space: normal;
    overflow: hidden;
    word-wrap: break-word;
    direction: ltr;
    padding: 2px 3px 2px 3px;
    }
    .ritz .waffle .s6 {
    background-color: #eeffcc;
    text-align: left;
    font-weight: bold;
    color: #666666;
    font-family: Arial;
    font-size: 9pt;
    vertical-align: top;
    white-space: nowrap;
    overflow: hidden;
    direction: ltr;
    padding: 2px 3px 2px 3px;
    }
    .ritz .waffle .s23 {
    background-color: #6ab0de;
    text-align: left;
    font-weight: bold;
    color: #000000;
    font-family: Arial;
    font-size: 15pt;
    vertical-align: top;
    white-space: nowrap;
    direction: ltr;
    padding: 2px 3px 2px 3px;
    }
    .ritz .waffle .s25 {
    background-color: #6ab0de;
    text-align: left;
    color: #000000;
    font-family: Arial;
    font-size: 15pt;
    vertical-align: top;
    white-space: nowrap;
    overflow: hidden;
    direction: ltr;
    padding: 2px 3px 2px 3px;
    }
    .ritz .waffle .s20 {
    background-color: #e7f2fa;
    text-align: left;
    font-style: italic;
    color: #1155cc;
    font-family: Arial;
    font-size: 10pt;
    vertical-align: top;
    white-space: normal;
    overflow: hidden;
    word-wrap: break-word;
    direction: ltr;
    padding: 2px 3px 2px 3px;
    }
    .ritz .waffle .s17 {
    background-color: #6ab0de;
    text-align: left;
    color: #000000;
    font-family: Arial;
    font-size: 13pt;
    vertical-align: top;
    white-space: nowrap;
    overflow: hidden;
    direction: ltr;
    padding: 2px 3px 2px 3px;
    }
    .ritz .waffle .s26 {
    background-color: #6ab0de;
    text-align: left;
    font-weight: bold;
    color: #000000;
    font-family: docs-Roboto, Arial;
    font-size: 15pt;
    vertical-align: top;
    white-space: nowrap;
    overflow: hidden;
    direction: ltr;
    padding: 2px 3px 2px 3px;
    }
    .ritz .waffle .s2 {
    background-color: #f0b37e;
    text-align: center;
    font-weight: bold;
    color: #ffffff;
    font-family: Arial;
    font-size: 12pt;
    vertical-align: middle;
    white-space: nowrap;
    overflow: hidden;
    direction: ltr;
    padding: 2px 3px 2px 3px;
    }
    .ritz .waffle .s12 {
    background-color: #eeffcc;
    text-align: left;
    color: #000000;
    font-family: Arial;
    font-size: 9pt;
    vertical-align: top;
    white-space: nowrap;
    overflow: hidden;
    direction: ltr;
    padding: 2px 3px 2px 3px;
    }
    .ritz .waffle .s10 {
    background-color: #6ab0de;
    text-align: left;
    color: #000000;
    font-family: Arial;
    font-size: 10pt;
    vertical-align: top;
    white-space: nowrap;
    direction: ltr;
    padding: 2px 3px 2px 3px;
    }
    .ritz .waffle .s1 {
    background-color: #f0b37e;
    text-align: left;
    font-weight: bold;
    color: #ffffff;
    font-family: Arial;
    font-size: 12pt;
    vertical-align: middle;
    white-space: nowrap;
    overflow: hidden;
    direction: ltr;
    padding: 2px 3px 2px 3px;
    }
    .ritz .waffle .s5 {
    background-color: #e7f2fa;
    text-align: left;
    font-weight: bold;
    color: #980000;
    font-family: Arial;
    font-size: 11pt;
    vertical-align: top;
    white-space: normal;
    overflow: hidden;
    word-wrap: break-word;
    direction: ltr;
    padding: 2px 3px 2px 3px;
    }
    .ritz .waffle .s15 {
    background-color: #6ab0de;
    text-align: left;
    font-weight: bold;
    color: #000000;
    font-family: Arial;
    font-size: 13pt;
    vertical-align: top;
    white-space: nowrap;
    direction: ltr;
    padding: 2px 3px 2px 3px;
    }
    .ritz .waffle .s21 {
    background-color: #eeffcc;
    text-align: left;
    text-decoration: underline;
    text-decoration-skip-ink: none;
    -webkit-text-decoration-skip: none;
    color: #1155cc;
    font-family: Arial;
    font-size: 10pt;
    vertical-align: top;
    white-space: nowrap;
    overflow: hidden;
    direction: ltr;
    padding: 2px 3px 2px 3px;
    }
    .ritz .waffle .s3 {
    background-color: #6ab0de;
    text-align: left;
    font-weight: bold;
    color: #ffffff;
    font-family: docs-Roboto, Arial;
    font-size: 12pt;
    vertical-align: top;
    white-space: normal;
    overflow: hidden;
    word-wrap: break-word;
    direction: ltr;
    padding: 2px 3px 2px 3px;
    }
    .ritz .waffle .s22 {
    background-color: #6ab0de;
    text-align: left;
    font-weight: bold;
    color: #ffffff;
    font-family: docs-Roboto, Arial;
    font-size: 15pt;
    vertical-align: top;
    white-space: normal;
    overflow: hidden;
    word-wrap: break-word;
    direction: ltr;
    padding: 2px 3px 2px 3px;
    }
    .ritz .waffle .s27 {
    background-color: #eeffcc;
    text-align: left;
    color: #666666;
    font-family: Arial;
    font-size: 9pt;
    vertical-align: top;
    white-space: nowrap;
    direction: ltr;
    padding: 2px 3px 2px 3px;
    }
    .ritz .waffle .s14 {
    background-color: #6ab0de;
    text-align: left;
    font-weight: bold;
    color: #ffffff;
    font-family: docs-Roboto, Arial;
    font-size: 13pt;
    vertical-align: top;
    white-space: normal;
    overflow: hidden;
    word-wrap: break-word;
    direction: ltr;
    padding: 2px 3px 2px 3px;
    }
    .ritz .waffle .s11 {
    background-color: #eeffcc;
    text-align: left;
    color: #000000;
    font-family: Arial;
    font-size: 10pt;
    vertical-align: top;
    white-space: nowrap;
    direction: ltr;
    padding: 2px 3px 2px 3px;
    }
    .ritz .waffle .s16 {
    background-color: #6ab0de;
    text-align: left;
    color: #000000;
    font-family: Arial;
    font-size: 13pt;
    vertical-align: top;
    white-space: nowrap;
    direction: ltr;
    padding: 2px 3px 2px 3px;
    }
    .ritz .waffle .s19 {
    background-color: #eeffcc;
    text-align: left;
    color: #000000;
    font-family: Arial;
    font-size: 10pt;
    vertical-align: top;
    white-space: nowrap;
    overflow: hidden;
    direction: ltr;
    padding: 2px 3px 2px 3px;
    }
    .ritz .waffle .s9 {
    background-color: #6ab0de;
    text-align: left;
    font-weight: bold;
    color: #000000;
    font-family: Arial;
    font-size: 10pt;
    vertical-align: top;
    white-space: nowrap;
    direction: ltr;
    padding: 2px 3px 2px 3px;
    }
    .ritz .waffle .s4 {
    background-color: #6ab0de;
    text-align: left;
    font-weight: bold;
    color: #000000;
    font-family: docs-Roboto, Arial;
    font-size: 11pt;
    vertical-align: top;
    white-space: nowrap;
    overflow: hidden;
    direction: ltr;
    padding: 2px 3px 2px 3px;
    }
    .ritz .waffle .s24 {
    background-color: #6ab0de;
    text-align: left;
    color: #000000;
    font-family: Arial;
    font-size: 15pt;
    vertical-align: top;
    white-space: nowrap;
    direction: ltr;
    padding: 2px 3px 2px 3px;
    }
    .ritz .waffle .s18 {
    background-color: #6ab0de;
    text-align: left;
    font-weight: bold;
    color: #000000;
    font-family: docs-Roboto, Arial;
    font-size: 13pt;
    vertical-align: top;
    white-space: nowrap;
    overflow: hidden;
    direction: ltr;
    padding: 2px 3px 2px 3px;
    }
    .ritz .waffle .s13 {
    background-color: #6ab0de;
    text-align: left;
    color: #000000;
    font-family: Arial;
    font-size: 10pt;
    vertical-align: top;
    white-space: nowrap;
    overflow: hidden;
    direction: ltr;
    padding: 2px 3px 2px 3px;
    }
    .ritz .waffle .s8 {
    background-color: #eeffcc;
    text-align: left;
    text-decoration: underline;
    text-decoration-skip-ink: none;
    -webkit-text-decoration-skip: none;
    color: #1155cc;
    font-family: Arial;
    font-size: 9pt;
    vertical-align: top;
    white-space: nowrap;
    overflow: hidden;
    direction: ltr;
    padding: 2px 3px 2px 3px;
    }
    .ritz .waffle .s7 {
    background-color: #eeffcc;
    text-align: left;
    color: #666666;
    font-family: Arial;
    font-size: 9pt;
    vertical-align: top;
    white-space: nowrap;
    overflow: hidden;
    direction: ltr;
    padding: 2px 3px 2px 3px;
    }
</style>
<div class="ritz grid-container" dir="ltr">
    <table class="waffle" cellspacing="0" cellpadding="0">
    <tbody>
        <tr style="height: 20px">
        <td class="s0"></td>
        <td class="s1" dir="ltr"></td>
        <td class="s2" dir="ltr">Cloud</td>
        <td class="s2" dir="ltr"></td>
        <td class="s2" dir="ltr"></td>
        <td class="s2" dir="ltr"></td>
        <td class="s2" dir="ltr">Reference</td>
        <td class="s2" dir="ltr"></td>
        <td class="s2" dir="ltr"></td>
        </tr>
        <tr style="height: 20px">
        <td class="s0"></td>
        <td class="s1" dir="ltr"></td>
        <td class="s2" dir="ltr">Amazon</td>
        <td class="s2" dir="ltr">Google</td>
        <td class="s2" dir="ltr">Azure</td>
        <td class="s2" dir="ltr">Others</td>
        <td class="s2" dir="ltr"></td>
        <td class="s2" dir="ltr"></td>
        <td class="s2" dir="ltr"></td>
        </tr>
        <tr style="height: 20px">
        <td class="s3" dir="ltr">System Design</td>
        <td class="s4" dir="ltr"></td>
        <td class="s4" dir="ltr"></td>
        <td class="s4" dir="ltr"></td>
        <td class="s4" dir="ltr"></td>
        <td class="s4" dir="ltr"></td>
        <td class="s4" dir="ltr"></td>
        <td class="s4" dir="ltr"></td>
        <td class="s4" dir="ltr"></td>
        </tr>
        <tr style="height: 20px">
        <td class="s5" dir="ltr">Architecture</td>
        <td class="s6" dir="ltr">Monolithic</td>
        <td class="s7" dir="ltr"></td>
        <td class="s7" dir="ltr"></td>
        <td class="s7" dir="ltr"></td>
        <td class="s7" dir="ltr"></td>
        <td class="s7" dir="ltr"></td>
        <td class="s7" dir="ltr"></td>
        <td class="s7" dir="ltr"></td>
        </tr>
        <tr style="height: 20px">
        <td class="s5" dir="ltr"></td>
        <td class="s6" dir="ltr">Microservices</td>
        <td class="s7" dir="ltr"></td>
        <td class="s7" dir="ltr"></td>
        <td class="s7" dir="ltr"></td>
        <td class="s7" dir="ltr"></td>
        <td class="s7" dir="ltr"></td>
        <td class="s7" dir="ltr"></td>
        <td class="s7" dir="ltr"></td>
        </tr>
        <tr style="height: 20px">
        <td class="s5" dir="ltr"></td>
        <td class="s6" dir="ltr">Modular monolithic application</td>
        <td class="s7" dir="ltr"></td>
        <td class="s7" dir="ltr"></td>
        <td class="s7" dir="ltr"></td>
        <td class="s7" dir="ltr"></td>
        <td class="s8" dir="ltr">
            <a
            target="_blank"
            href="https://medium.com/design-microservices-architecture-with-patterns/microservices-killer-modular-monolithic-architecture-ac83814f6862"
            >https://medium.com/design-microservices-architecture-with-patterns/microservices-killer-modular-monolithic-architecture-ac83814f6862<br /></a
            ><a
            target="_blank"
            href="https://github.com/kgrzybek/modular-monolith-with-ddd/tree/master"
            >https://github.com/kgrzybek/modular-monolith-with-ddd/tree/master</a
            >
        </td>
        <td class="s7" dir="ltr"></td>
        <td class="s7" dir="ltr"></td>
        </tr>
        <tr style="height: 20px">
        <td class="s5" dir="ltr">communication patterns</td>
        <td class="s6" dir="ltr">
            Synchronous communication<br />Asynchronous communication
        </td>
        <td class="s7" dir="ltr"></td>
        <td class="s7" dir="ltr"></td>
        <td class="s7" dir="ltr"></td>
        <td class="s7" dir="ltr"></td>
        <td class="s8" dir="ltr"></td>
        <td class="s7" dir="ltr"></td>
        <td class="s7" dir="ltr"></td>
        </tr>
        <tr style="height: 20px">
        <td class="s3" dir="ltr">Externalized Configuration</td>
        <td class="s9"></td>
        <td class="s10"></td>
        <td class="s10"></td>
        <td class="s10"></td>
        <td class="s10"></td>
        <td class="s10"></td>
        <td class="s10"></td>
        <td class="s10"></td>
        </tr>
        <tr style="height: 20px">
        <td class="s5" dir="ltr">Servers</td>
        <td class="s6" dir="ltr">
            Spring Cloud Config Server<br />etcd<span style="color: #ff0000"
            >(47.2k)</span
            ><br />Consul KV<span style="color: #ff0000">(28.2k)</span>
        </td>
        <td class="s11"></td>
        <td class="s11"></td>
        <td class="s7" dir="ltr">Azure App Configuration</td>
        <td class="s11"></td>
        <td class="s8" dir="ltr">
            <a
            target="_blank"
            href="https://docs.google.com/document/d/13GErfIAvRysUwPR2kfcfRkM2a8GZptlP4cNAmKTjedw/edit#heading=h.7oqivix51g6a"
            >https://docs.google.com/document/d/13GErfIAvRysUwPR2kfcfRkM2a8GZptlP4cNAmKTjedw/edit#heading=h.7oqivix51g6a</a
            >
        </td>
        <td class="s11"></td>
        <td class="s11"></td>
        </tr>
        <tr style="height: 20px">
        <td class="s5" dir="ltr">Libraries</td>
        <td class="s6" dir="ltr">
            Spring Cloud Config <br />Spring Cloud Consul Config
        </td>
        <td class="s11"></td>
        <td class="s11"></td>
        <td class="s11"></td>
        <td class="s11"></td>
        <td class="s12" dir="ltr"></td>
        <td class="s11"></td>
        <td class="s11"></td>
        </tr>
        <tr style="height: 20px">
        <td class="s3" dir="ltr">Secret Management</td>
        <td class="s10"></td>
        <td class="s10"></td>
        <td class="s10"></td>
        <td class="s10"></td>
        <td class="s10"></td>
        <td class="s10"></td>
        <td class="s10"></td>
        <td class="s10"></td>
        </tr>
        <tr style="height: 20px">
        <td class="s5" dir="ltr">Servers</td>
        <td class="s6" dir="ltr">
            HashiCorp Vault<span style="color: #ff0000">(30.8k)<br /></span
            ><span style="color: #000000">sops</span
            ><span style="color: #ff0000">(16.2k)</span><br />Kubernetes
            Secrets<br />OpenShift secrets<br />Docker secrets
        </td>
        <td class="s11" dir="ltr">AWS Secret Manager</td>
        <td class="s11" dir="ltr">GCP Secret Manager</td>
        <td class="s7" dir="ltr">Azure Key Vault</td>
        <td class="s11"></td>
        <td class="s8"></td>
        <td class="s11"></td>
        <td class="s11"></td>
        </tr>
        <tr style="height: 20px">
        <td class="s5" dir="ltr">Libraries</td>
        <td class="s6" dir="ltr">Spring Cloud Config</td>
        <td class="s11"></td>
        <td class="s11"></td>
        <td class="s11"></td>
        <td class="s11"></td>
        <td class="s12" dir="ltr"></td>
        <td class="s11"></td>
        <td class="s11"></td>
        </tr>
        <tr style="height: 20px">
        <td class="s3" dir="ltr">Proxy</td>
        <td class="s9"></td>
        <td class="s10"></td>
        <td class="s10"></td>
        <td class="s10"></td>
        <td class="s10"></td>
        <td class="s13"></td>
        <td class="s4" dir="ltr"></td>
        <td class="s4" dir="ltr"></td>
        </tr>
        <tr style="height: 20px">
        <td class="s5" dir="ltr">Servers</td>
        <td class="s6" dir="ltr">
            Envoy<span style="color: #ff0000">(24.5k)<br /></span>Nginx<span
            style="color: #ff0000"
            >(21k)</span
            ><br />HAProxy<span style="color: #ff0000">(4.7k)</span
            ><br />Apache HTTP Server
        </td>
        <td class="s7" dir="ltr"></td>
        <td class="s7" dir="ltr"></td>
        <td class="s7" dir="ltr"></td>
        <td class="s7" dir="ltr"></td>
        <td class="s8" dir="ltr">
            <a
            target="_blank"
            href="https://docs.google.com/document/d/13GErfIAvRysUwPR2kfcfRkM2a8GZptlP4cNAmKTjedw/edit#heading=h.7oqivix51g6a"
            >https://docs.google.com/document/d/13GErfIAvRysUwPR2kfcfRkM2a8GZptlP4cNAmKTjedw/edit#heading=h.7oqivix51g6a</a
            >
        </td>
        <td class="s7" dir="ltr"></td>
        <td class="s7" dir="ltr"></td>
        </tr>
        <tr style="height: 20px">
        <td class="s3" dir="ltr">Gateway</td>
        <td class="s9"></td>
        <td class="s10"></td>
        <td class="s10"></td>
        <td class="s10"></td>
        <td class="s10"></td>
        <td class="s13"></td>
        <td class="s4" dir="ltr"></td>
        <td class="s4" dir="ltr"></td>
        </tr>
        <tr style="height: 20px">
        <td class="s5" dir="ltr">Servers</td>
        <td class="s6" dir="ltr">
            Spring Cloud Gateway<span style="color: #ff0000">(4.5k)</span
            ><br />Consul API Gateway<span style="color: #ff0000"
            >(28.2k)<br /></span
            >Nginx<span style="color: #ff0000">(21k)<br /></span
            ><span style="color: #000000">Apache APISIX</span
            ><span style="color: #ff0000">(14.2k)</span><br />HAProxy<span
            style="color: #ff0000"
            >(4.7k)</span
            ><br />Apache HTTP Server<br />F5<br />Kong Gateway<span
            style="color: #ff0000"
            >(38.7k)</span
            ><br />traefik
        </td>
        <td class="s7" dir="ltr">Amazon API Gateway</td>
        <td class="s7" dir="ltr">Google Cloud API Gateway</td>
        <td class="s7" dir="ltr">Azure API Management.</td>
        <td class="s7" dir="ltr"></td>
        <td class="s8" dir="ltr">
            <a
            target="_blank"
            href="https://docs.google.com/document/d/13GErfIAvRysUwPR2kfcfRkM2a8GZptlP4cNAmKTjedw/edit#heading=h.7oqivix51g6a"
            >https://docs.google.com/document/d/13GErfIAvRysUwPR2kfcfRkM2a8GZptlP4cNAmKTjedw/edit#heading=h.7oqivix51g6a</a
            >
        </td>
        <td class="s7" dir="ltr"></td>
        <td class="s7" dir="ltr"></td>
        </tr>
        <tr style="height: 20px">
        <td class="s3" dir="ltr">Health</td>
        <td class="s9"></td>
        <td class="s10"></td>
        <td class="s10"></td>
        <td class="s10"></td>
        <td class="s10"></td>
        <td class="s13"></td>
        <td class="s4" dir="ltr"></td>
        <td class="s4" dir="ltr"></td>
        </tr>
        <tr style="height: 20px">
        <td class="s5" dir="ltr">Servers</td>
        <td class="s6" dir="ltr">Spring Cloud Consul<br />Consul</td>
        <td class="s7" dir="ltr"></td>
        <td class="s7" dir="ltr"></td>
        <td class="s7" dir="ltr"></td>
        <td class="s7" dir="ltr"></td>
        <td class="s8" dir="ltr">
            <a
            target="_blank"
            href="https://docs.google.com/document/d/13GErfIAvRysUwPR2kfcfRkM2a8GZptlP4cNAmKTjedw/edit#heading=h.lzjmqc2ca4s5"
            >https://docs.google.com/document/d/13GErfIAvRysUwPR2kfcfRkM2a8GZptlP4cNAmKTjedw/edit#heading=h.lzjmqc2ca4s5</a
            >
        </td>
        <td class="s7" dir="ltr"></td>
        <td class="s7" dir="ltr"></td>
        </tr>
        <tr style="height: 20px">
        <td class="s5" dir="ltr">Libraries</td>
        <td class="s6" dir="ltr">Spring Boot Actuator</td>
        <td class="s7" dir="ltr"></td>
        <td class="s7" dir="ltr"></td>
        <td class="s7" dir="ltr"></td>
        <td class="s7" dir="ltr"></td>
        <td class="s12" dir="ltr"></td>
        <td class="s7" dir="ltr"></td>
        <td class="s7" dir="ltr"></td>
        </tr>
        <tr style="height: 20px">
        <td class="s5" dir="ltr">circuit breaker</td>
        <td class="s6" dir="ltr">Resilience4j<br /></td>
        <td class="s7" dir="ltr"></td>
        <td class="s7" dir="ltr"></td>
        <td class="s7" dir="ltr"></td>
        <td class="s7" dir="ltr"></td>
        <td class="s12" dir="ltr"></td>
        <td class="s7" dir="ltr"></td>
        <td class="s7" dir="ltr"></td>
        </tr>
        <tr style="height: 20px">
        <td class="s3" dir="ltr">Service Discovery</td>
        <td class="s9"></td>
        <td class="s10"></td>
        <td class="s10"></td>
        <td class="s10"></td>
        <td class="s10"></td>
        <td class="s13"></td>
        <td class="s4" dir="ltr"></td>
        <td class="s4" dir="ltr"></td>
        </tr>
        <tr style="height: 20px">
        <td class="s5" dir="ltr">Servers</td>
        <td class="s6" dir="ltr">
            Spring Cloud Consul<br />Consul<br />Eureka,<br />Zookeeper
        </td>
        <td class="s7" dir="ltr"></td>
        <td class="s7" dir="ltr"></td>
        <td class="s7" dir="ltr"></td>
        <td class="s7" dir="ltr"></td>
        <td class="s8" dir="ltr">
            <a
            target="_blank"
            href="https://docs.google.com/document/d/13GErfIAvRysUwPR2kfcfRkM2a8GZptlP4cNAmKTjedw/edit#heading=h.lzjmqc2ca4s5"
            >https://docs.google.com/document/d/13GErfIAvRysUwPR2kfcfRkM2a8GZptlP4cNAmKTjedw/edit#heading=h.lzjmqc2ca4s5</a
            >
        </td>
        <td class="s7" dir="ltr"></td>
        <td class="s7" dir="ltr"></td>
        </tr>
        <tr style="height: 20px">
        <td class="s5" dir="ltr">Libraries</td>
        <td class="s6" dir="ltr">Spring Cloud Consul,Consul</td>
        <td class="s7" dir="ltr"></td>
        <td class="s7" dir="ltr"></td>
        <td class="s7" dir="ltr"></td>
        <td class="s7" dir="ltr"></td>
        <td class="s12" dir="ltr"></td>
        <td class="s7" dir="ltr"></td>
        <td class="s7" dir="ltr"></td>
        </tr>
        <tr style="height: 20px">
        <td class="s3" dir="ltr">Load Balancing</td>
        <td class="s9"></td>
        <td class="s10"></td>
        <td class="s10"></td>
        <td class="s10"></td>
        <td class="s10"></td>
        <td class="s13"></td>
        <td class="s4" dir="ltr"></td>
        <td class="s4" dir="ltr"></td>
        </tr>
        <tr style="height: 20px">
        <td class="s5" dir="ltr">Servers</td>
        <td class="s6" dir="ltr">
            Spring Cloud Load Balancer+Consul<br />traefik
        </td>
        <td class="s7" dir="ltr"></td>
        <td class="s7" dir="ltr"></td>
        <td class="s7" dir="ltr"></td>
        <td class="s7" dir="ltr"></td>
        <td class="s8" dir="ltr">
            <a
            target="_blank"
            href="https://docs.google.com/document/d/13GErfIAvRysUwPR2kfcfRkM2a8GZptlP4cNAmKTjedw/edit#heading=h.nm5eslswusp5"
            >https://docs.google.com/document/d/13GErfIAvRysUwPR2kfcfRkM2a8GZptlP4cNAmKTjedw/edit#heading=h.nm5eslswusp5</a
            >
        </td>
        <td class="s7" dir="ltr"></td>
        <td class="s7" dir="ltr"></td>
        </tr>
        <tr style="height: 20px">
        <td class="s5" dir="ltr">Libraries</td>
        <td class="s6" dir="ltr">Spring Cloud Load Balancer<br /></td>
        <td class="s7" dir="ltr"></td>
        <td class="s7" dir="ltr"></td>
        <td class="s7" dir="ltr"></td>
        <td class="s7" dir="ltr"></td>
        <td class="s12" dir="ltr"></td>
        <td class="s7" dir="ltr"></td>
        <td class="s7" dir="ltr"></td>
        </tr>
        <tr style="height: 20px">
        <td class="s14" dir="ltr">Security</td>
        <td class="s15"></td>
        <td class="s16"></td>
        <td class="s16"></td>
        <td class="s16"></td>
        <td class="s16"></td>
        <td class="s17"></td>
        <td class="s18" dir="ltr"></td>
        <td class="s18" dir="ltr"></td>
        </tr>
        <tr style="height: 20px">
        <td class="s5" dir="ltr">Servers</td>
        <td class="s6" dir="ltr">
            Keycloak<br />Red Hat build of Keycloak<br />
        </td>
        <td class="s7" dir="ltr">Cognito</td>
        <td class="s7" dir="ltr"></td>
        <td class="s7" dir="ltr">Azure AD</td>
        <td class="s7" dir="ltr">Okta</td>
        <td class="s12" dir="ltr"></td>
        <td class="s7" dir="ltr"></td>
        <td class="s7" dir="ltr"></td>
        </tr>
        <tr style="height: 20px">
        <td class="s5" dir="ltr">Libraries</td>
        <td class="s6" dir="ltr">Spring Security<br />Apache Shiro</td>
        <td class="s7" dir="ltr"></td>
        <td class="s7" dir="ltr"></td>
        <td class="s7" dir="ltr"></td>
        <td class="s7" dir="ltr"></td>
        <td class="s12" dir="ltr"></td>
        <td class="s7" dir="ltr"></td>
        <td class="s7" dir="ltr"></td>
        </tr>
        <tr style="height: 20px">
        <td class="s14" dir="ltr">Development</td>
        <td class="s15"></td>
        <td class="s16"></td>
        <td class="s16"></td>
        <td class="s16"></td>
        <td class="s16"></td>
        <td class="s17"></td>
        <td class="s18" dir="ltr"></td>
        <td class="s18" dir="ltr"></td>
        </tr>
        <tr style="height: 20px">
        <td class="s5" dir="ltr">IDE</td>
        <td class="s6" dir="ltr">Vscode,IntelliJ IDEA ,Eclipse</td>
        <td class="s11"></td>
        <td class="s11"></td>
        <td class="s11"></td>
        <td class="s11"></td>
        <td class="s19"></td>
        <td class="s4" dir="ltr"></td>
        <td class="s4" dir="ltr"></td>
        </tr>
        <tr style="height: 20px">
        <td class="s5">Code Generation</td>
        <td class="s6" dir="ltr">Lombok</td>
        <td class="s11"></td>
        <td class="s11"></td>
        <td class="s11"></td>
        <td class="s11"></td>
        <td class="s19"></td>
        <td class="s4" dir="ltr"></td>
        <td class="s4" dir="ltr"></td>
        </tr>
        <tr style="height: 20px">
        <td class="s5" dir="ltr">HTTP and API testing client</td>
        <td class="s6" dir="ltr">HTTPie,Postman</td>
        <td class="s11"></td>
        <td class="s11"></td>
        <td class="s11"></td>
        <td class="s11"></td>
        <td class="s19"></td>
        <td class="s11"></td>
        <td class="s11"></td>
        </tr>
        <tr style="height: 20px">
        <td class="s5">App secrets</td>
        <td class="s6" dir="ltr">Environment variables</td>
        <td class="s11"></td>
        <td class="s11"></td>
        <td class="s11"></td>
        <td class="s11"></td>
        <td class="s8"></td>
        <td class="s11"></td>
        <td class="s11"></td>
        </tr>
        <tr style="height: 20px">
        <td class="s14" dir="ltr">DB</td>
        <td class="s15"></td>
        <td class="s16"></td>
        <td class="s16"></td>
        <td class="s16"></td>
        <td class="s16"></td>
        <td class="s17"></td>
        <td class="s18" dir="ltr"></td>
        <td class="s18" dir="ltr"></td>
        </tr>
        <tr style="height: 20px">
        <td class="s5" dir="ltr">Choosing a database</td>
        <td class="s6" dir="ltr"></td>
        <td class="s7" dir="ltr"></td>
        <td class="s7" dir="ltr"></td>
        <td class="s7" dir="ltr"></td>
        <td class="s7" dir="ltr"></td>
        <td class="s8" dir="ltr">
            <a
            target="_blank"
            href="https://docs.google.com/document/d/13GErfIAvRysUwPR2kfcfRkM2a8GZptlP4cNAmKTjedw/edit#bookmark=id.3yud5bry6zx"
            >https://docs.google.com/document/d/13GErfIAvRysUwPR2kfcfRkM2a8GZptlP4cNAmKTjedw/edit#bookmark=id.3yud5bry6zx</a
            >
        </td>
        <td class="s7" dir="ltr"></td>
        <td class="s7" dir="ltr"></td>
        </tr>
        <tr style="height: 20px">
        <td class="s20" dir="ltr">RDBMS(SQL)</td>
        <td class="s6" dir="ltr">
            SQL Server<br />SQLite<br />PostgreSQL<br />MySQL<br />Oracle DB
        </td>
        <td class="s7" dir="ltr"></td>
        <td class="s7" dir="ltr"></td>
        <td class="s7" dir="ltr"></td>
        <td class="s7" dir="ltr"></td>
        <td class="s7" dir="ltr">
            <span
            style="
                text-decoration: underline;
                text-decoration-skip-ink: none;
                -webkit-text-decoration-skip: none;
                color: #1155cc;
            "
            ><a
                target="_blank"
                href="https://docs.google.com/document/d/13GErfIAvRysUwPR2kfcfRkM2a8GZptlP4cNAmKTjedw/edit#heading=h.bkzz6vg3t8ro"
                >https://docs.google.com/document/d/13GErfIAvRysUwPR2kfcfRkM2a8GZptlP4cNAmKTjedw/edit#heading=h.bkzz6vg3t8ro</a
            ></span
            >o
        </td>
        <td class="s7" dir="ltr"></td>
        <td class="s7" dir="ltr"></td>
        </tr>
        <tr style="height: 20px">
        <td class="s20" dir="ltr">NoSQL</td>
        <td class="s6" dir="ltr">MongoDB<br />Elasticsearch</td>
        <td class="s7" dir="ltr">Azure Cosmos DB</td>
        <td class="s7" dir="ltr"></td>
        <td class="s7" dir="ltr"></td>
        <td class="s7" dir="ltr"></td>
        <td class="s7" dir="ltr"></td>
        <td class="s7" dir="ltr"></td>
        <td class="s7" dir="ltr"></td>
        </tr>
        <tr style="height: 20px">
        <td class="s5" dir="ltr">ORM</td>
        <td class="s6" dir="ltr">
            Hibernate ORM<br />OpenJPA <br />EclipseLink <br />DataNucleus
        </td>
        <td class="s7" dir="ltr"></td>
        <td class="s7" dir="ltr"></td>
        <td class="s7" dir="ltr"></td>
        <td class="s7" dir="ltr"></td>
        <td class="s7" dir="ltr"></td>
        <td class="s7" dir="ltr"></td>
        <td class="s7" dir="ltr"></td>
        </tr>
        <tr style="height: 20px">
        <td class="s5" dir="ltr">Higher-level migration tools</td>
        <td class="s6" dir="ltr">Liquibase<br />Flyway</td>
        <td class="s7" dir="ltr"></td>
        <td class="s7" dir="ltr"></td>
        <td class="s7" dir="ltr"></td>
        <td class="s7" dir="ltr"></td>
        <td class="s7" dir="ltr"></td>
        <td class="s7" dir="ltr"></td>
        <td class="s7" dir="ltr"></td>
        </tr>
        <tr style="height: 20px">
        <td class="s5" dir="ltr">Helper Libraries</td>
        <td class="s6" dir="ltr">querydsl</td>
        <td class="s7" dir="ltr"></td>
        <td class="s7" dir="ltr"></td>
        <td class="s7" dir="ltr"></td>
        <td class="s7" dir="ltr"></td>
        <td class="s7" dir="ltr"></td>
        <td class="s7" dir="ltr"></td>
        <td class="s7" dir="ltr"></td>
        </tr>
        <tr style="height: 20px">
        <td class="s3" dir="ltr">Frontend</td>
        <td class="s9"></td>
        <td class="s10"></td>
        <td class="s10"></td>
        <td class="s10"></td>
        <td class="s10"></td>
        <td class="s10"></td>
        <td class="s10"></td>
        <td class="s10"></td>
        </tr>
        <tr style="height: 20px">
        <td class="s5" dir="ltr">Frameworks</td>
        <td class="s6" dir="ltr">Angular<br />React<br />Vue</td>
        <td class="s7" dir="ltr"></td>
        <td class="s7" dir="ltr"></td>
        <td class="s7" dir="ltr"></td>
        <td class="s7" dir="ltr"></td>
        <td class="s7" dir="ltr"></td>
        <td class="s7" dir="ltr"></td>
        <td class="s7" dir="ltr"></td>
        </tr>
        <tr style="height: 20px">
        <td class="s5" dir="ltr">Testing</td>
        <td class="s6" dir="ltr"></td>
        <td class="s7" dir="ltr"></td>
        <td class="s7" dir="ltr"></td>
        <td class="s7" dir="ltr"></td>
        <td class="s7" dir="ltr"></td>
        <td class="s7" dir="ltr"></td>
        <td class="s7" dir="ltr"></td>
        <td class="s7" dir="ltr"></td>
        </tr>
        <tr style="height: 20px">
        <td class="s20" dir="ltr">Libraries</td>
        <td class="s6" dir="ltr">Mirage<br />Mocha</td>
        <td class="s11"></td>
        <td class="s11"></td>
        <td class="s11"></td>
        <td class="s11"></td>
        <td class="s19"></td>
        <td class="s11"></td>
        <td class="s11"></td>
        </tr>
        <tr style="height: 20px">
        <td class="s14" dir="ltr">Web</td>
        <td class="s15"></td>
        <td class="s16"></td>
        <td class="s16"></td>
        <td class="s16"></td>
        <td class="s16"></td>
        <td class="s17"></td>
        <td class="s18" dir="ltr"></td>
        <td class="s18" dir="ltr"></td>
        </tr>
        <tr style="height: 20px">
        <td class="s5" dir="ltr">API Frameworks</td>
        <td class="s6" dir="ltr">Spring Boot</td>
        <td class="s7" dir="ltr"></td>
        <td class="s7" dir="ltr"></td>
        <td class="s7" dir="ltr"></td>
        <td class="s7" dir="ltr"></td>
        <td class="s7" dir="ltr"></td>
        <td class="s7" dir="ltr"></td>
        <td class="s7" dir="ltr"></td>
        </tr>
        <tr style="height: 20px">
        <td class="s5" dir="ltr">Caching</td>
        <td class="s6" dir="ltr"></td>
        <td class="s7" dir="ltr"></td>
        <td class="s7" dir="ltr"></td>
        <td class="s7" dir="ltr"></td>
        <td class="s7" dir="ltr"></td>
        <td class="s7" dir="ltr"></td>
        <td class="s7" dir="ltr"></td>
        <td class="s7" dir="ltr"></td>
        </tr>
        <tr style="height: 20px">
        <td class="s20" dir="ltr">Server-side caching<br /></td>
        <td class="s6" dir="ltr">Memcached, Redis, Couchbase,Infinispan</td>
        <td class="s7" dir="ltr"></td>
        <td class="s7" dir="ltr"></td>
        <td class="s7" dir="ltr"></td>
        <td class="s7" dir="ltr"></td>
        <td class="s7" dir="ltr"></td>
        <td class="s7" dir="ltr">
            A caching system that saves data to key/value stores by using
            either a built-in service or a third-party provider
        </td>
        <td class="s7" dir="ltr"></td>
        </tr>
        <tr style="height: 20px">
        <td class="s20" dir="ltr">Client-side caching</td>
        <td class="s6" dir="ltr"></td>
        <td class="s7" dir="ltr"></td>
        <td class="s7" dir="ltr"></td>
        <td class="s7" dir="ltr"></td>
        <td class="s7" dir="ltr"></td>
        <td class="s7" dir="ltr"></td>
        <td class="s7" dir="ltr">
            A caching mechanism defined in the HTTP specifications that relies
            on several HTTP response headers (including Expires,
            Cache-Control, Last-Modified, and ETag) that can be set from the
            server to control the caching behavior of the clients
        </td>
        <td class="s7" dir="ltr"></td>
        </tr>
        <tr style="height: 20px">
        <td class="s20" dir="ltr">Intermediate caching</td>
        <td class="s6" dir="ltr"></td>
        <td class="s7" dir="ltr">Cloudflare</td>
        <td class="s7" dir="ltr"></td>
        <td class="s7" dir="ltr"></td>
        <td class="s7" dir="ltr"></td>
        <td class="s7" dir="ltr"></td>
        <td class="s7" dir="ltr">
            (also known as proxy caching, reverse-proxy caching, or
            content-delivery network [CDN] caching)—A response-caching
            technique that stores cached data by using dedicated services
            (proxies) and/or relies on third-party services optimized for
            accelerated and geographically distributed content distribution
            (CDN providers), following the same HTTP header-based rules as
            client-side caching
        </td>
        <td class="s7" dir="ltr">
            When implementing intermediate caching, we are basically creating
            “cached copies” of some URL-related content (HTML pages, JSON
            data, binary files, and so on) that typically become accessible
            regardless of any authentication and authorization logic used by
            the server to render that content in the first request/response
            cycle. As a general rule, intermediate caching services should be
            used to cache only publicly available content and resources,
            leaving restricted and personal data to private caching approaches
            (or no-cache) to prevent potentially critical data security
            problems
        </td>
        </tr>
        <tr style="height: 20px">
        <td class="s5" dir="ltr">API documentation</td>
        <td class="s6" dir="ltr">Swashbuckle</td>
        <td class="s7" dir="ltr"></td>
        <td class="s7" dir="ltr"></td>
        <td class="s7" dir="ltr"></td>
        <td class="s7" dir="ltr"></td>
        <td class="s7" dir="ltr"></td>
        <td class="s7" dir="ltr"></td>
        <td class="s7" dir="ltr"></td>
        </tr>
        <tr style="height: 20px">
        <td class="s5" dir="ltr"></td>
        <td class="s6" dir="ltr">NSwag</td>
        <td class="s7" dir="ltr"></td>
        <td class="s7" dir="ltr"></td>
        <td class="s7" dir="ltr"></td>
        <td class="s7" dir="ltr"></td>
        <td class="s7" dir="ltr"></td>
        <td class="s7" dir="ltr"></td>
        <td class="s7" dir="ltr"></td>
        </tr>
        <tr style="height: 20px">
        <td class="s5" dir="ltr">API versioning</td>
        <td class="s6" dir="ltr">
        </td>
        <td class="s7" dir="ltr"></td>
        <td class="s7" dir="ltr"></td>
        <td class="s7" dir="ltr"></td>
        <td class="s7" dir="ltr"></td>
        <td class="s7" dir="ltr"></td>
        <td class="s7" dir="ltr"></td>
        <td class="s7" dir="ltr"></td>
        </tr>
        <tr style="height: 20px">
        <td class="s14" dir="ltr">Logging</td>
        <td class="s15"></td>
        <td class="s16"></td>
        <td class="s16"></td>
        <td class="s16"></td>
        <td class="s16"></td>
        <td class="s17"></td>
        <td class="s18" dir="ltr"></td>
        <td class="s18" dir="ltr"></td>
        </tr>
        <tr style="height: 20px">
        <td class="s5" dir="ltr">Logging API</td>
        <td class="s6" dir="ltr">SLF4J</td>
        <td class="s7" dir="ltr"></td>
        <td class="s7" dir="ltr"></td>
        <td class="s7" dir="ltr"></td>
        <td class="s7" dir="ltr"></td>
        <td class="s12" dir="ltr"></td>
        <td class="s7" dir="ltr"></td>
        <td class="s7" dir="ltr"></td>
        </tr>
        <tr style="height: 20px">
        <td class="s5" dir="ltr">Logging Frameworks</td>
        <td class="s6" dir="ltr">
            Log4j,java.util.logging, reload4j , <br />Apache Commons
            Logging(JCL),LogBack
        </td>
        <td class="s7" dir="ltr"></td>
        <td class="s7" dir="ltr"></td>
        <td class="s7" dir="ltr"></td>
        <td class="s7" dir="ltr"></td>
        <td class="s12" dir="ltr"></td>
        <td class="s7" dir="ltr"></td>
        <td class="s7" dir="ltr"></td>
        </tr>
        <tr style="height: 20px">
        <td class="s5" dir="ltr">Log aggregation</td>
        <td class="s6" dir="ltr">
            logstash <br />Splunk<br />Datadog <br />grafana loki<br />Fluentd<br />Graylog
        </td>
        <td class="s7" dir="ltr">Amazon CloudWatch</td>
        <td class="s7" dir="ltr"></td>
        <td class="s7" dir="ltr"></td>
        <td class="s7" dir="ltr"></td>
        <td class="s12" dir="ltr"></td>
        <td class="s7" dir="ltr"></td>
        <td class="s7" dir="ltr"></td>
        </tr>
        <tr style="height: 26px">
        <td class="s14" dir="ltr">Monitoring</td>
        <td class="s15"></td>
        <td class="s16"></td>
        <td class="s16"></td>
        <td class="s16"></td>
        <td class="s16"></td>
        <td class="s17"></td>
        <td class="s18" dir="ltr"></td>
        <td class="s18" dir="ltr"></td>
        </tr>
        <tr style="height: 20px">
        <td class="s5" dir="ltr">Servers</td>
        <td class="s6" dir="ltr">
            Prometheus(<span style="color: #ff0000">54.7k)</span><br />Apache
            Skywalking<span style="color: #ff0000">(23.6k)<br /></span
            >ElasticSearch<br />Opentelemetry
        </td>
        <td class="s11" dir="ltr">AWS CloudWatch</td>
        <td class="s11"></td>
        <td class="s11"></td>
        <td class="s11"></td>
        <td class="s19" dir="ltr"></td>
        <td class="s11"></td>
        <td class="s11"></td>
        </tr>
        <tr style="height: 20px">
        <td class="s5" dir="ltr">Frameworks</td>
        <td class="s6" dir="ltr"></td>
        <td class="s11" dir="ltr"></td>
        <td class="s11"></td>
        <td class="s11"></td>
        <td class="s11"></td>
        <td class="s19" dir="ltr"></td>
        <td class="s11"></td>
        <td class="s11"></td>
        </tr>
        <tr style="height: 20px">
        <td class="s14" dir="ltr">Tracing<br /></td>
        <td class="s15"></td>
        <td class="s16"></td>
        <td class="s16"></td>
        <td class="s16"></td>
        <td class="s16"></td>
        <td class="s17"></td>
        <td class="s18" dir="ltr"></td>
        <td class="s18" dir="ltr"></td>
        </tr>
        <tr style="height: 20px">
        <td class="s5" dir="ltr">Servers</td>
        <td class="s6" dir="ltr">
            Grafana Tempo<br />Zipkin<br />Apache Skywalking(23.6k)
        </td>
        <td class="s7" dir="ltr">AWS CloudWatch</td>
        <td class="s7" dir="ltr"></td>
        <td class="s7" dir="ltr"></td>
        <td class="s7" dir="ltr"></td>
        <td class="s12" dir="ltr"></td>
        <td class="s7" dir="ltr"></td>
        <td class="s7" dir="ltr"></td>
        </tr>
        <tr style="height: 20px">
        <td class="s5" dir="ltr">Frameworks</td>
        <td class="s6" dir="ltr">Spring Cloud Sleuth</td>
        <td class="s7" dir="ltr"></td>
        <td class="s7" dir="ltr"></td>
        <td class="s7" dir="ltr"></td>
        <td class="s7" dir="ltr"></td>
        <td class="s12" dir="ltr"></td>
        <td class="s7" dir="ltr"></td>
        <td class="s7" dir="ltr"></td>
        </tr>
        <tr style="height: 20px">
        <td class="s14" dir="ltr">Message Queuing</td>
        <td class="s15"></td>
        <td class="s16"></td>
        <td class="s16"></td>
        <td class="s16"></td>
        <td class="s16"></td>
        <td class="s17"></td>
        <td class="s18" dir="ltr"></td>
        <td class="s18" dir="ltr"></td>
        </tr>
        <tr style="height: 20px">
        <td class="s5" dir="ltr">Server</td>
        <td class="s6" dir="ltr">
            RabbitMQ<br />Apache Kafka<br />Apache Pulsar<br />Apache RocketMQ
        </td>
        <td class="s11"></td>
        <td class="s11"></td>
        <td class="s11"></td>
        <td class="s11"></td>
        <td class="s21" dir="ltr">
            <a
            target="_blank"
            href="https://docs.google.com/document/d/13GErfIAvRysUwPR2kfcfRkM2a8GZptlP4cNAmKTjedw/edit#heading=h.7oqivix51g6a"
            >https://docs.google.com/document/d/13GErfIAvRysUwPR2kfcfRkM2a8GZptlP4cNAmKTjedw/edit#heading=h.o0fy3fdgu5ks</a
            >
        </td>
        <td class="s11"></td>
        <td class="s11"></td>
        </tr>
        <tr style="height: 20px">
        <td class="s5" dir="ltr">AMQP message converters</td>
        <td class="s6" dir="ltr">
            JSON,XML,Google’s Protocol Buffers (protobuf)
        </td>
        <td class="s11"></td>
        <td class="s11"></td>
        <td class="s11"></td>
        <td class="s11"></td>
        <td class="s21" dir="ltr">
            <a
            target="_blank"
            href="https://docs.google.com/document/d/13GErfIAvRysUwPR2kfcfRkM2a8GZptlP4cNAmKTjedw/edit#heading=h.s71m2t3h3q5y"
            >https://docs.google.com/document/d/13GErfIAvRysUwPR2kfcfRkM2a8GZptlP4cNAmKTjedw/edit#heading=h.s71m2t3h3q5y</a
            >
        </td>
        <td class="s11"></td>
        <td class="s11"></td>
        </tr>
        <tr style="height: 20px">
        <td class="s5" dir="ltr">transactions</td>
        <td class="s6" dir="ltr">local ,global (distributed)</td>
        <td class="s11"></td>
        <td class="s11"></td>
        <td class="s11"></td>
        <td class="s11"></td>
        <td class="s21" dir="ltr">
            <a
            target="_blank"
            href="https://docs.google.com/document/d/13GErfIAvRysUwPR2kfcfRkM2a8GZptlP4cNAmKTjedw/edit#heading=h.hbuaras3xbor"
            >https://docs.google.com/document/d/13GErfIAvRysUwPR2kfcfRkM2a8GZptlP4cNAmKTjedw/edit#heading=h.hbuaras3xbor</a
            >
        </td>
        <td class="s11"></td>
        <td class="s11"></td>
        </tr>
        <tr style="height: 20px">
        <td class="s14" dir="ltr">Testing</td>
        <td class="s15"></td>
        <td class="s16"></td>
        <td class="s16"></td>
        <td class="s16"></td>
        <td class="s16"></td>
        <td class="s17"></td>
        <td class="s18" dir="ltr"></td>
        <td class="s18" dir="ltr"></td>
        </tr>
        <tr style="height: 20px">
        <td class="s5" dir="ltr">Test-Driven Development</td>
        <td class="s6"></td>
        <td class="s11"></td>
        <td class="s11"></td>
        <td class="s11"></td>
        <td class="s11"></td>
        <td class="s19"></td>
        <td class="s11"></td>
        <td class="s11"></td>
        </tr>
        <tr style="height: 20px">
        <td class="s20" dir="ltr">Unit Testing Frameworks</td>
        <td class="s6" dir="ltr">
            Spring Test libraries (included via Spring Boot Test starter)<br />JUnit
            5<br />TestNG
        </td>
        <td class="s11"></td>
        <td class="s11"></td>
        <td class="s11"></td>
        <td class="s11"></td>
        <td class="s19"></td>
        <td class="s11"></td>
        <td class="s11"></td>
        </tr>
        <tr style="height: 20px">
        <td class="s20" dir="ltr">Mocking frameworks</td>
        <td class="s6" dir="ltr">Spring @MockBean,Mockito</td>
        <td class="s11"></td>
        <td class="s11"></td>
        <td class="s11"></td>
        <td class="s11"></td>
        <td class="s19"></td>
        <td class="s11"></td>
        <td class="s11"></td>
        </tr>
        <tr style="height: 20px">
        <td class="s20" dir="ltr">Assertions frameworks</td>
        <td class="s6" dir="ltr">JUnit 5 assertions,AssertJ</td>
        <td class="s11"></td>
        <td class="s11"></td>
        <td class="s11"></td>
        <td class="s11"></td>
        <td class="s19"></td>
        <td class="s11"></td>
        <td class="s11"></td>
        </tr>
        <tr style="height: 20px">
        <td class="s20" dir="ltr">Functional Testing Frameworks</td>
        <td class="s6" dir="ltr"></td>
        <td class="s11"></td>
        <td class="s11"></td>
        <td class="s11"></td>
        <td class="s11"></td>
        <td class="s19"></td>
        <td class="s11"></td>
        <td class="s11"></td>
        </tr>
        <tr style="height: 20px">
        <td class="s20" dir="ltr">End-to-end Testing Frameworks</td>
        <td class="s6" dir="ltr"></td>
        <td class="s11"></td>
        <td class="s11"></td>
        <td class="s11"></td>
        <td class="s11"></td>
        <td class="s19"></td>
        <td class="s11"></td>
        <td class="s11"></td>
        </tr>
        <tr style="height: 20px">
        <td class="s20" dir="ltr">Integration Testing Frameworks</td>
        <td class="s6" dir="ltr"></td>
        <td class="s11"></td>
        <td class="s11"></td>
        <td class="s11"></td>
        <td class="s11"></td>
        <td class="s19"></td>
        <td class="s11"></td>
        <td class="s11"></td>
        </tr>
        <tr style="height: 20px">
        <td class="s5" dir="ltr">Behavior-Driven Development</td>
        <td class="s6"></td>
        <td class="s11"></td>
        <td class="s11"></td>
        <td class="s11"></td>
        <td class="s11"></td>
        <td class="s19"></td>
        <td class="s11"></td>
        <td class="s11"></td>
        </tr>
        <tr style="height: 20px">
        <td class="s20" dir="ltr">Frameworks</td>
        <td class="s6" dir="ltr">Cucumber</td>
        <td class="s11"></td>
        <td class="s11"></td>
        <td class="s11"></td>
        <td class="s11"></td>
        <td class="s19"></td>
        <td class="s11"></td>
        <td class="s11"></td>
        </tr>
        <tr style="height: 20px">
        <td class="s5" dir="ltr">Frontend</td>
        <td class="s6"></td>
        <td class="s11"></td>
        <td class="s11"></td>
        <td class="s11"></td>
        <td class="s11"></td>
        <td class="s19"></td>
        <td class="s11"></td>
        <td class="s11"></td>
        </tr>
        <tr style="height: 20px">
        <td class="s14" dir="ltr">Continuous Integration</td>
        <td class="s15"></td>
        <td class="s16"></td>
        <td class="s16"></td>
        <td class="s16"></td>
        <td class="s16"></td>
        <td class="s17"></td>
        <td class="s18" dir="ltr"></td>
        <td class="s18" dir="ltr"></td>
        </tr>
        <tr style="height: 20px">
        <td class="s5" dir="ltr">Server</td>
        <td class="s6" dir="ltr">
            Jenkins<br />Bamboo<br />GitLab CI<br />CircleCI
        </td>
        <td class="s11"></td>
        <td class="s11"></td>
        <td class="s11"></td>
        <td class="s11"></td>
        <td class="s19" dir="ltr"></td>
        <td class="s11"></td>
        <td class="s11"></td>
        </tr>
        <tr style="height: 20px">
        <td class="s14" dir="ltr">Tools and Libs</td>
        <td class="s15"></td>
        <td class="s16"></td>
        <td class="s16"></td>
        <td class="s16"></td>
        <td class="s16"></td>
        <td class="s17"></td>
        <td class="s18" dir="ltr"></td>
        <td class="s18" dir="ltr"></td>
        </tr>
        <tr style="height: 20px">
        <td class="s5" dir="ltr">reporting</td>
        <td class="s6"></td>
        <td class="s11"></td>
        <td class="s11"></td>
        <td class="s11"></td>
        <td class="s11"></td>
        <td class="s19"></td>
        <td class="s11"></td>
        <td class="s11"></td>
        </tr>
        <tr style="height: 20px">
        <td class="s14" dir="ltr">API Integration</td>
        <td class="s15"></td>
        <td class="s16"></td>
        <td class="s16"></td>
        <td class="s16"></td>
        <td class="s16"></td>
        <td class="s17"></td>
        <td class="s18" dir="ltr"></td>
        <td class="s18" dir="ltr"></td>
        </tr>
        <tr style="height: 20px">
        <td class="s5" dir="ltr">Payment processing</td>
        <td class="s6" dir="ltr">Stripe API</td>
        <td class="s11"></td>
        <td class="s11"></td>
        <td class="s11"></td>
        <td class="s11"></td>
        <td class="s19"></td>
        <td class="s11"></td>
        <td class="s11"></td>
        </tr>
        <tr style="height: 20px">
        <td class="s5" dir="ltr"></td>
        <td class="s6"></td>
        <td class="s11"></td>
        <td class="s11"></td>
        <td class="s11"></td>
        <td class="s11"></td>
        <td class="s19"></td>
        <td class="s11"></td>
        <td class="s11"></td>
        </tr>
        <tr style="height: 20px">
        <td class="s14" dir="ltr">Production</td>
        <td class="s15"></td>
        <td class="s16"></td>
        <td class="s16"></td>
        <td class="s16"></td>
        <td class="s16"></td>
        <td class="s17"></td>
        <td class="s18" dir="ltr"></td>
        <td class="s18" dir="ltr"></td>
        </tr>
        <tr style="height: 20px">
        <td class="s5" dir="ltr">App secrets</td>
        <td class="s6" dir="ltr">Environment variables</td>
        <td class="s7" dir="ltr">Azure Key Vault</td>
        <td class="s7" dir="ltr"></td>
        <td class="s7" dir="ltr"></td>
        <td class="s7" dir="ltr"></td>
        <td class="s7" dir="ltr"></td>
        <td class="s7" dir="ltr"></td>
        <td class="s7" dir="ltr"></td>
        </tr>
        <tr style="height: 20px">
        <td class="s14" dir="ltr">Deploy</td>
        <td class="s15"></td>
        <td class="s16"></td>
        <td class="s16"></td>
        <td class="s16"></td>
        <td class="s16"></td>
        <td class="s17"></td>
        <td class="s18" dir="ltr"></td>
        <td class="s18" dir="ltr"></td>
        </tr>
        <tr style="height: 20px">
        <td class="s5" dir="ltr">Containerization</td>
        <td class="s6" dir="ltr"></td>
        <td class="s7" dir="ltr"></td>
        <td class="s7" dir="ltr"></td>
        <td class="s7" dir="ltr"></td>
        <td class="s7" dir="ltr"></td>
        <td class="s7" dir="ltr"></td>
        <td class="s7" dir="ltr"></td>
        <td class="s7" dir="ltr"></td>
        </tr>
        <tr style="height: 20px">
        <td class="s22" dir="ltr">Cloud-Native Microservices</td>
        <td class="s23"></td>
        <td class="s24"></td>
        <td class="s24"></td>
        <td class="s24"></td>
        <td class="s24"></td>
        <td class="s25"></td>
        <td class="s26" dir="ltr"></td>
        <td class="s26" dir="ltr"></td>
        </tr>
        <tr style="height: 20px">
        <td class="s5" dir="ltr">Container Platforms</td>
        <td class="s6" dir="ltr">
            Kubernetes<br />Apache Mesos<br />Docker Swarm
        </td>
        <td class="s11"></td>
        <td class="s11"></td>
        <td class="s11"></td>
        <td class="s11"></td>
        <td class="s19"></td>
        <td class="s11"></td>
        <td class="s11"></td>
        </tr>
        <tr style="height: 20px">
        <td class="s5" dir="ltr">Application Platforms</td>
        <td class="s6" dir="ltr">Heroku<br />CloudFoundry</td>
        <td class="s11"></td>
        <td class="s11"></td>
        <td class="s11"></td>
        <td class="s11"></td>
        <td class="s19"></td>
        <td class="s11"></td>
        <td class="s11"></td>
        </tr>
        <tr style="height: 20px">
        <td class="s5" dir="ltr">Cloud Providers</td>
        <td class="s6" dir="ltr">
            AWS<br />Google<br />Azure<br />OpenShift
        </td>
        <td class="s11"></td>
        <td class="s11"></td>
        <td class="s11"></td>
        <td class="s11"></td>
        <td class="s19"></td>
        <td class="s11"></td>
        <td class="s11"></td>
        </tr>
        <tr style="height: 20px">
        <td class="s3" dir="ltr"></td>
        <td class="s4" dir="ltr"></td>
        <td class="s4" dir="ltr"></td>
        <td class="s4" dir="ltr"></td>
        <td class="s4" dir="ltr"></td>
        <td class="s4" dir="ltr"></td>
        <td class="s4" dir="ltr"></td>
        <td class="s4" dir="ltr"></td>
        <td class="s4" dir="ltr"></td>
        </tr>
        <tr style="height: 20px">
        <td class="s5" dir="ltr"></td>
        <td class="s6" dir="ltr"></td>
        <td class="s7" dir="ltr"></td>
        <td class="s7" dir="ltr"></td>
        <td class="s7" dir="ltr"></td>
        <td class="s7" dir="ltr"></td>
        <td class="s7" dir="ltr"></td>
        <td class="s7" dir="ltr"></td>
        <td class="s7" dir="ltr"></td>
        </tr>
        <tr style="height: 20px">
        <td class="s5" dir="ltr"></td>
        <td class="s6" dir="ltr"></td>
        <td class="s7" dir="ltr"></td>
        <td class="s7" dir="ltr"></td>
        <td class="s7" dir="ltr"></td>
        <td class="s7" dir="ltr"></td>
        <td class="s7" dir="ltr"></td>
        <td class="s7" dir="ltr"></td>
        <td class="s7" dir="ltr"></td>
        </tr>
        <tr style="height: 20px">
        <td class="s3" dir="ltr"></td>
        <td class="s4" dir="ltr"></td>
        <td class="s4" dir="ltr"></td>
        <td class="s4" dir="ltr"></td>
        <td class="s4" dir="ltr"></td>
        <td class="s4" dir="ltr"></td>
        <td class="s4" dir="ltr"></td>
        <td class="s4" dir="ltr"></td>
        <td class="s4" dir="ltr"></td>
        </tr>
        <tr style="height: 20px">
        <td class="s5" dir="ltr"></td>
        <td class="s6" dir="ltr"></td>
        <td class="s7" dir="ltr"></td>
        <td class="s7" dir="ltr"></td>
        <td class="s7" dir="ltr"></td>
        <td class="s7" dir="ltr"></td>
        <td class="s7" dir="ltr"></td>
        <td class="s7" dir="ltr"></td>
        <td class="s7" dir="ltr"></td>
        </tr>
        <tr style="height: 20px">
        <td class="s5" dir="ltr"></td>
        <td class="s6" dir="ltr"></td>
        <td class="s7" dir="ltr"></td>
        <td class="s7" dir="ltr"></td>
        <td class="s7" dir="ltr"></td>
        <td class="s7" dir="ltr"></td>
        <td class="s7" dir="ltr"></td>
        <td class="s7" dir="ltr"></td>
        <td class="s7" dir="ltr"></td>
        </tr>
        <tr style="height: 20px">
        <td class="s5" dir="ltr"></td>
        <td class="s6" dir="ltr"></td>
        <td class="s7" dir="ltr"></td>
        <td class="s7" dir="ltr"></td>
        <td class="s7" dir="ltr"></td>
        <td class="s7" dir="ltr"></td>
        <td class="s7" dir="ltr"></td>
        <td class="s7" dir="ltr"></td>
        <td class="s7" dir="ltr"></td>
        </tr>
        <tr style="height: 20px">
        <td class="s5" dir="ltr"></td>
        <td class="s6" dir="ltr"></td>
        <td class="s27" dir="ltr"></td>
        <td class="s27" dir="ltr"></td>
        <td class="s27" dir="ltr"></td>
        <td class="s27" dir="ltr"></td>
        <td class="s7" dir="ltr"></td>
        <td class="s27" dir="ltr"></td>
        <td class="s27" dir="ltr"></td>
        </tr>
        <tr style="height: 20px">
        <td class="s5" dir="ltr"></td>
        <td class="s6" dir="ltr"></td>
        <td class="s7" dir="ltr"></td>
        <td class="s7" dir="ltr"></td>
        <td class="s7" dir="ltr"></td>
        <td class="s7" dir="ltr"></td>
        <td class="s7" dir="ltr"></td>
        <td class="s7" dir="ltr"></td>
        <td class="s7" dir="ltr"></td>
        </tr>
        <tr style="height: 20px">
        <td class="s5" dir="ltr"></td>
        <td class="s6" dir="ltr"></td>
        <td class="s7" dir="ltr"></td>
        <td class="s7" dir="ltr"></td>
        <td class="s7" dir="ltr"></td>
        <td class="s7" dir="ltr"></td>
        <td class="s7" dir="ltr"></td>
        <td class="s7" dir="ltr"></td>
        <td class="s7" dir="ltr"></td>
        </tr>
        <tr style="height: 20px">
        <td class="s5" dir="ltr"></td>
        <td class="s6" dir="ltr"></td>
        <td class="s7" dir="ltr"></td>
        <td class="s7" dir="ltr"></td>
        <td class="s7" dir="ltr"></td>
        <td class="s7" dir="ltr"></td>
        <td class="s7" dir="ltr"></td>
        <td class="s7" dir="ltr"></td>
        <td class="s7" dir="ltr"></td>
        </tr>
        <tr style="height: 20px">
        <td class="s5" dir="ltr"></td>
        <td class="s6" dir="ltr"></td>
        <td class="s7" dir="ltr"></td>
        <td class="s7" dir="ltr"></td>
        <td class="s7" dir="ltr"></td>
        <td class="s7" dir="ltr"></td>
        <td class="s7" dir="ltr"></td>
        <td class="s7" dir="ltr"></td>
        <td class="s7" dir="ltr"></td>
        </tr>
    </tbody>
    </table>
</div>

