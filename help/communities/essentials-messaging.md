---
title: Grondbeginselen van berichten
description: Leer over de details van het werken met en het gebruiken van de component van het Overseinen om een overseineneigenschap op een website te omvatten.
contentOwner: Guillaume Carlino
products: SG_EXPERIENCEMANAGER/6.5/COMMUNITIES
topic-tags: developing
content-type: reference
docset: aem65
exl-id: b941b5e0-f768-4393-9a9d-ded2cd7d10c4
solution: Experience Manager
feature: Communities
role: Admin
source-git-commit: 1f56c99980846400cfde8fa4e9a55e885bc2258d
workflow-type: tm+mt
source-wordcount: '362'
ht-degree: 0%

---

# Grondbeginselen van berichten {#messaging-essentials}

Deze pagina documenteert de details van het werken met het gebruiken van de component van het Overseinen om een overseineneigenschap op een website te omvatten.

## Essentiële elementen voor client-kant {#essentials-for-client-side}

**Bericht samenstellen**

<table>
 <tbody>
  <tr>
   <td> <strong>resourceType</strong></td>
   <td><p>social/messaging/components/hbs/composemessement</p> </td>
  </tr>
  <tr>
   <td> <a href="/help/communities/client-customize.md#clientlibs-for-scf" target="_blank"><strong>clientllibs</strong></a></td>
   <td><p>cq.social.hbs.messaging</p> </td>
  </tr>
  <tr>
   <td> <strong>sjablonen</strong></td>
   <td>/libs/social/messaging/components/hbs/composemessage/composemessage.hbs</td>
  </tr>
  <tr>
   <td><strong>css</strong></td>
   <td>/libs/social/messaging/components/hbs/composemessage/clientlibs/composemessage.css</td>
  </tr>
  <tr>
   <td><strong>eigenschappen</strong></td>
   <td>Zie <a href="/help/communities/configure-messaging.md" target="_blank">Berichten configureren</a></td>
  </tr>
  <tr>
   <td><strong>beheerdersconfiguratie</strong></td>
   <td><a href="/help/communities/messaging.md">Berichten configureren</a></td>
  </tr>
 </tbody>
</table>

**Berichtlijst**

(Voor Postvak IN, Verzonden en Prullenbak)

<table>
 <tbody>
  <tr>
   <td> <strong>resourceType</strong></td>
   <td><p>social/messaging/components/hbs/messagebox</p> </td>
  </tr>
  <tr>
   <td> <a href="/help/communities/client-customize.md#clientlibs-for-scf" target="_blank"><strong>clientllibs</strong></a></td>
   <td><p>cq.social.hbs.messaging</p> </td>
  </tr>
  <tr>
   <td> <strong>sjablonen</strong></td>
   <td>/libs/social/messaging/components/hbs/messagebox/messagebox.hbs</td>
  </tr>
  <tr>
   <td><strong>css</strong></td>
   <td>/libs/social/messaging/components/hbs/messagebox/clientlibs/messagebox.css</td>
  </tr>
  <tr>
   <td><strong>eigenschappen</strong></td>
   <td>Zie <a href="/help/communities/configure-messaging.md" target="_blank">Berichten configureren</a></td>
  </tr>
  <tr>
   <td><strong>beheerdersconfiguratie</strong></td>
   <td><a href="/help/communities/messaging.md" target="_blank">Berichten configureren</a></td>
  </tr>
 </tbody>
</table>

Zie ook [Aanpassingen aan de clientzijde](/help/communities/client-customize.md)

## Essentiële elementen voor server-side {#essentials-for-server-side}

* [Berichten configureren](/help/communities/configure-messaging.md)
* [Berichtenclient-API&#39;s](https://developer.adobe.com/experience-manager/reference-materials/6-5/javadoc/com/adobe/cq/social/messaging/client/api/package-summary.html) voor SCF-componenten
* [Berichten-API&#39;s](https://developer.adobe.com/experience-manager/reference-materials/6-5/javadoc/com/adobe/cq/social/messaging/api/package-summary.html) voor de dienst
* [Eindpunten van berichten](https://developer.adobe.com/experience-manager/reference-materials/6-5/javadoc/com/adobe/cq/social/messaging/client/endpoints/package-summary.html)
* [Aanpassingen op de server](/help/communities/server-customize.md)

>[!CAUTION]
>
>De parameter String moet *niet* bevat een slash &quot;/&quot; voor de volgende MessageBuilder-methoden:
>
>* `setInboxPath`()
>* `setSentItemsPath`()
>
>Bijvoorbeeld:
>
>```
>valid: mb.setInboxPath( "/mail/inbox" );
> not valid: mb.setInboxPath( "/mail/inbox/" );
>```

### Community-site {#community-site}

Een community-sitestructuur die met de wizard is gemaakt, bevat de berichtfunctie wanneer deze is geselecteerd. Zie `User Management` instellingen van [Community-siteconsole](/help/communities/sites-console.md#user-management).

### Voorbeeldcode: bericht ontvangen {#sample-code-message-received-notification}

Met de functie Sociaal overseinen worden bijvoorbeeld gebeurtenissen voor bewerkingen gegenereerd. `send`, `marking read`, `marking delete`. Deze gebeurtenissen kunnen worden afgevangen en er kunnen acties worden ondernomen op basis van de gegevens in de gebeurtenis.

Het volgende voorbeeld is een gebeurtenishandler die luistert naar de gebeurtenis `message sent` en verzendt een e-mail naar alle berichtontvangers met behulp van de `Day CQ Mail Service`.

Om het server-zijsteekproefmanuscript te proberen, hebt u een ontwikkelomgeving en de capaciteit nodig om een bundel te bouwen OSGi:

1. Aanmelden als beheerder ` [CRXDE|Lite](https://localhost:4502/crx/de)`.
1. Een `bundle node`in `/apps/engage/install` met willekeurige namen, zoals:

   * Symbolische naam: `com.engage.media.social.messaging.MessagingNotification`
   * Naam: bericht Aan de slag
   * Beschrijving: een voorbeeldservice voor het verzenden van een e-mailbericht aan gebruikers wanneer zij een bericht ontvangen
   * Pakket: `com.engage.media.social.messaging.notification`

1. Navigeren naar `/apps/engage/install/com.engage.media.social.messaging.MessagingNotification/src/main/java/com/engage/media/social/messaging/notification`en vervolgens:

   1. Verwijder de `Activator.java` automatisch aangemaakt.
   1. Klasse maken `MessageEventHandler.java`.
   1. De onderstaande code kopiëren en plakken in `MessageEventHandler.java`.

1. Klikken **Alles opslaan**.
1. Navigeren naar `/apps/engage/install/com.engage.media.social.messaging.MessagingNotification/com.engage.media.social.messaging.MessagingNotification.bnd`en voegt u alle instructies voor het importeren toe, zoals in het dialoogvenster `MessageEventHandler.java` code.
1. Bouw de bundel.
1. Zorgen `Day CQ Mail Service`De dienst OSGi wordt gevormd.
1. Meld u aan als demogebruiker en stuur een e-mail naar een andere gebruiker.
1. De ontvanger ontvangt een e-mail met betrekking tot een nieuw bericht.

#### MessageEventHandler.java {#messageeventhandler-java}

```java
package com.engage.media.social.messaging.notification;

import org.apache.felix.scr.annotations.Component;
import org.apache.felix.scr.annotations.Properties;
import org.apache.felix.scr.annotations.Property;
import org.apache.felix.scr.annotations.Service;
import org.apache.felix.scr.annotations.Reference;
import org.apache.sling.api.resource.ResourceResolver;
import org.apache.sling.api.resource.ResourceResolverFactory;
import org.apache.sling.api.resource.Resource;
import org.apache.commons.mail.Email;
import org.apache.commons.mail.EmailException;
import org.apache.commons.mail.SimpleEmail;
import org.apache.commons.mail.HtmlEmail;
import java.util.List;
import org.osgi.service.event.Event;
import org.osgi.service.event.EventHandler;
import org.slf4j.Logger;
import org.slf4j.LoggerFactory;
import com.adobe.cq.social.messaging.api.Message;
import com.adobe.cq.social.messaging.api.MessagingEvent;
import com.day.cq.mailer.MessageGatewayService;
import com.day.cq.mailer.MessageGateway;

@Component(immediate=true)
@Service(EventHandler.class)
@Properties({
        @Property(name = "event.topics", value = "com/adobe/cq/social/message")
})
public class MessagingEventHandler implements EventHandler {
    private Logger logger = LoggerFactory.getLogger(MessagingEventHandler.class);

    @Reference
    ResourceResolverFactory resourceResolverFactory;

    @Reference
    private MessageGatewayService messageGatewayService;

    ResourceResolver resourceResolver=null;
    MessageGateway messageGateway=null;

    public void sendMail(String from, String to,String subject, String content){
        Email email = new SimpleEmail();
        messageGateway = messageGatewayService.getGateway(SimpleEmail.class);
        try {
         email.addTo(to);
            email.addReplyTo(from);
            email.setFrom(from);
            email.setMsg(content);
            email.setSubject(subject);
         messageGateway.send(email);
        } catch(EmailException ex) {
            logger.error("MessageNotificaiton : Error sending email : "+ex.getMessage());
        }
        logger.info("**** MessageNotification **** Mail sent to " + to);
    }

    public void handleEvent(Event event) {
        //Get Message Path and originator User's ID from event
        String messagePath = (String) event.getProperty("path");
        String senderId = (String) event.getProperty("userId");
        MessagingEvent.MessagingActions action = (MessagingEvent.MessagingActions) event.getProperty("action");
        try{
            if(MessagingEvent.MessagingActions.MessageSent.equals(action)){
                resourceResolver = resourceResolverFactory.getAdministrativeResourceResolver(null);

                //Read message
                Resource resource = resourceResolver.getResource(messagePath);
                Message msg = resource.adaptTo(Message.class);

                //Get list of recipient Ids from message
                //For Getting Started Tutorial, Id is same as email. If that is not the case in your site,
                //an additional step is needed to retrieve the email for the Id
                List<String> reclist = msg.getRecipientIdList();
                for(int i=0;i<reclist.size();i++){
                    //Send Email using Mailing Service
                    sendMail("admin@cqadmin.qqq",reclist.get(i),"New message on Getting Started Tutorial", "Hi\nYou have received a new message from  " +  senderId + ". To read it, sign in to Getting Started Tutorial.\n\n-Engage Admin");
                }
            }
        } catch(Exception ex){
            logger.error("Error getting message info : " + ex.getMessage());
        } finally {
            resourceResolver.close();
        }

    }
}
```
