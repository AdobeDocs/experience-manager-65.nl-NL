---
title: OSGi Events for Communities Components
seo-title: OSGi Events for Communities Components
description: OSGi-gebeurtenissen worden verzonden die asynchrone listeners kunnen activeren
seo-description: OSGi-gebeurtenissen worden verzonden die asynchrone listeners kunnen activeren
uuid: 317e2add-689d-4c99-ae38-0703b6649cb7
contentOwner: msm-service
products: SG_EXPERIENCEMANAGER/6.5/COMMUNITIES
topic-tags: developing
content-type: reference
discoiquuid: 25b7ac08-6cdc-4dd5-a756-d6169b86f9ab
translation-type: tm+mt
source-git-commit: c897f034edbdbeee74869165ed384c3408a857e0
workflow-type: tm+mt
source-wordcount: '679'
ht-degree: 1%

---


# OSGi Events for Communities Components  {#osgi-events-for-communities-components}

## Overzicht {#overview}

Wanneer leden met de eigenschappen van de Gemeenschappen in wisselwerking staan, worden de gebeurtenissen OSGi verzonden die asynchrone luisteraars, zoals berichten of gamificatie (het scoren en het merken) kunnen teweegbrengen.

De [instantie SocialEvent](https://helpx.adobe.com/experience-manager/6-5/sites/developing/using/reference-materials/javadoc/com/adobe/cq/social/scf/core/SocialEvent.html) van een component registreert de gebeurtenissen als `actions` die voor een `topic`. De SocialEvent bevat een methode om een aan de actie `verb` gekoppeld item te retourneren. Er is een *n-1* relatie tussen `actions` en `verbs`.

Voor de onderdelen van Communities die in de release worden geleverd, wordt in de volgende tabellen de `verbs` definitie van elke `topic` beschikbare versie beschreven.

## Onderwerpen en werven {#topics-and-verbs}

[Agenda Component](calendar-basics-for-developers.md)SocialEvent `topic`= com/adobe/cq/social/agenda

| **Verb** | **Beschrijving** |
|---|---|
| POST | Lid maakt een kalendergebeurtenis |
| TOEVOEGEN | Opmerkingen van de lidstaten over een kalendergebeurtenis |
| BIJWERKEN | De agendagebeurtenis of de opmerking van het lid wordt bewerkt |
| DELETE | De agendagebeurtenis of de opmerking van het lid wordt verwijderd |

[Opmerkingen Component](essentials-comments.md)SocialEvent `topic`= com/adobe/cq/social/comment

| **Verb** | **Beschrijving** |
|---|---|
| POST | Lid maakt een opmerking |
| TOEVOEGEN | Antwoorden van de lidstaten op opmerkingen |
| BIJWERKEN | Opmerking van lid wordt bewerkt |
| DELETE | Opmerking van lid wordt verwijderd |

[File Library Component](essentials-file-library.md)SocialEvent `topic`= com/adobe/cq/social/fileLibrary

| **Verb** | **Beschrijving** |
|---|---|
| POST | Lid maakt een map |
| ATTACH | Lid uploadt een bestand |
| BIJWERKEN | Lid werkt een omslag of een dossier bij |
| DELETE | Lid verwijdert een map of bestand |

[Forum Component](essentials-forum.md)SocialEvent `topic`= com/adobe/cq/social/forum

| **Verb** | **Beschrijving** |
|---|---|
| POST | Lid maakt het forum |
| TOEVOEGEN | Antwoorden van de lidstaten op het forum |
| BIJWERKEN | Het onderwerp of antwoord van het forum van het lid wordt bewerkt |
| DELETE | Het onderwerp of antwoord van het lid in het forum wordt verwijderd |

[Journal Component](blog-developer-basics.md)SocialEvent `topic`= com/adobe/cq/social/journaal

| **Verb** | **Beschrijving** |
|---|---|
| POST | Lid maakt een blogartikel |
| TOEVOEGEN | Opmerkingen van leden over blogartikelen |
| BIJWERKEN | Blogartikel of commentaar van lid wordt bewerkt |
| DELETE | Blogartikel of commentaar van lid wordt verwijderd |

[QnA Component](qna-essentials.md)SocialEvent `topic` = com/adobe/cq/social/qna

| **Verb** | **Beschrijving** |
|---|---|
| POST | Lid maakt een QnA-vraag |
| TOEVOEGEN | Lid maakt een antwoord op vraag |
| BIJWERKEN | Vraag of antwoord van lid wordt bewerkt |
| SELECT | Antwoord van lid is geselecteerd |
| SELECTEREN OPHEFFEN | Het antwoord van het lid is niet geselecteerd |
| DELETE | Vraag of antwoord van lid wordt verwijderd |

[Reviews Component](reviews-basics.md)SocialEvent `topic`= com/adobe/cq/social/review

| **Verb** | **Beschrijving** |
|---|---|
| POST | Lid leidt tot herziening |
| BIJWERKEN | Revisie van lid wordt bewerkt |
| DELETE | Herziening door lid wordt verwijderd |

[Beoordelingscomponent](rating-basics.md)SocialEvent `topic`= com/adobe/cq/social/tally

| **Verb** | **Beschrijving** |
|---|---|
| WAARDERING TOEVOEGEN | De inhoud van het lid is vervangen |
| RATING VERWIJDEREN | De inhoud van het lid is verlaagd |

[Stemcomponent](essentials-voting.md)SocialEvent `topic`= com/adobe/cq/social/tally

| **Verb** | **Beschrijving** |
|---|---|
| STEMMING TOEVOEGEN | Er is gestemd over de inhoud van het lid |
| STEMMING VERWIJDEREN | Over de inhoud van het lid is gestemd |

**Moderation-enabled Components** SocialEvent `topic`= com/adobe/cq/social/moderation

| **Verb** | **Beschrijving** |
|---|---|
| DENKEN | De inhoud van het lid wordt geweigerd |
| VLAG ALS ONJUIST | Inhoud van lid is gemarkeerd |
| ONGESCHIKTE LAG ALS ONJUIST | Inhoud van lid is niet gemarkeerd |
| ACCEPTEREN | De inhoud van het lid wordt goedgekeurd door moderator |
| SLUITEN | Lid sluit commentaar op bewerkingen en reacties |
| OPENEN | Opmerking voor opnieuw openen van lid |

## Gebeurtenissen voor aangepaste componenten {#events-for-custom-components}

Voor een aangepaste component moet de abstracte klasse [](https://helpx.adobe.com/experience-manager/6-5/sites/developing/using/reference-materials/javadoc/com/adobe/cq/social/scf/core/SocialEvent.html) SocialEvent worden uitgebreid om de gebeurtenissen van de component op te nemen zoals `actions`die voor een `topic`.

De aangepaste gebeurtenis zou de methode overschrijven, `getVerb()` zodat voor elke gebeurtenis een geschikte methode `verb`wordt geretourneerd `action`. De `verb` geretourneerde waarde voor een handeling kan een veelgebruikte (zoals `POST`) of een speciale waarde voor de component (zoals `ADD RATING`) zijn. Er is een *n-1* relatie tussen `actions`en `verbs`.

>[!NOTE]
>
>Zorg ervoor dat een aangepaste extensie is geregistreerd met een lagere rangschikking dan een bestaande implementatie in het product.


### Pseudo-code voor gebeurtenis Custom Component {#pseudo-code-for-custom-component-event}

[org.osgi.service.event.Event](https://osgi.org/javadoc/r4v41/org/osgi/service/event/Event.html);
[com.adobe.cq.social.scf.core.SocialEvent](https://helpx.adobe.com/experience-manager/6-5/sites/developing/using/reference-materials/javadoc/com/adobe/cq/social/scf/core/SocialEvent.html);
[com.adobe.granite.activity.streams.ObjectTypes](https://helpx.adobe.com/experience-manager/6-5/sites/developing/using/reference-materials/javadoc/com/adobe/granite/activitystreams/ObjectTypes.html);
[com.adobe.granite.activity streams.Verbs](https://helpx.adobe.com/experience-manager/6-5/sites/developing/using/reference-materials/javadoc/com/adobe/granite/activitystreams/Verbs.html);

```java
package com.mycompany.recipe;

import org.osgi.service.event.Event;
import com.adobe.cq.social.scf.core.SocialEvent;
import com.adobe.granite.activitystreams.ObjectTypes;
import com.adobe.granite.activitystreams.Verbs;

/*
 * The Recipe type, passed to RecipeEvent(), would be a custom Recipe class
 * that extends either
 * com.adobe.cq.social.scf.SocialComponent
 * or
 * com.adobe.cq.social.scf.SocialCollectionComponent
 * See https://docs.adobe.com/docs/en/aem/6-2/develop/communities/scf/server-customize.html
 */

/**
 * Defines events that are triggered on a custom component, "Recipe".
 */
public class RecipeEvent extends SocialEvent<RecipeEvent.RecipeActions> {

    private static final long serialVersionUID = 1L;
    protected static final String PARENT_PATH = "PARENT_PATH";

    /**
     * The event topic suffix for Recipe events
     */
    public static final String RECIPE_TOPIC = "recipe";

    /**
     * @param recipe - the recipe resource on which the event was triggered
     * @param userId - the user id of the user who triggered the action
     * @param action - the recipe action that triggered this event
     */
    public RecipeEvent(final Recipe recipe, final String userId, final RecipeEvent.RecipeActions action) {
        String recipePath = recipe.getResource().getPath();
        String parentPath = (recipe.getParentComponent() != null) ?
                             recipe.getParentComponent().getResource().getPath() :
                             recipe.getSourceComponentId();
        this(recipePath, userId, parentPath, action);
    }

    /**
     * @param recipePath - the path to the recipe resource (jcr node) on which the event was triggered
     * @param userId - the user id of the user who triggered the action
     * @param parentPath - the path to the parent node of the recipe resource
     * @param action - the recipe action that triggered this event
     */
    public RecipeEvent(final String recipePath, final String userId, final String parentPath) {
        super(RECIPE_TOPIC, recipePath, userId, action,
              new BaseEventObject(recipePath, ObjectTypes.ARTICLE),
              new BaseEventObject(parentPath, ObjectTypes.COLLECTION),
              new HashMap<String, Object>(1) {
            private static final long serialVersionUID = 1L;
            {
                if (parentPath != null) {
                    this.put(PARENT_PATH, parentPath);
                }

            }
        });
    }

    private RecipeEvent (final Event event) {
      super(event);
    }

    /**
     * List of available recipe actions that can trigger a recipe event.
     */
    public static enum RecipeActions implements SocialEvent.SocialActions {
        RecipeAdded,
        RecipeModified,
        RecipeDeleted;

        @Override
        public String getVerb() {
            switch (this) {
                case RecipeAdded:
                    return Verbs.POST;
                case RecipeModified:
                    return Verbs.UPDATE;
                case RecipeDeleted:
                    return Verbs.DELETE;
                default:
                    throw new IllegalArgumentException("Unsupported action");
            }
        }
    }

}
```

## Voorbeeld van gebeurtenislistener om activiteitsstroomgegevens te filteren {#sample-eventlistener-to-filter-activity-stream-data}

Het is mogelijk naar gebeurtenissen te luisteren om te wijzigen wat er in de activiteitsstroom wordt weergegeven.

Het volgende pseudo-codevoorbeeld verwijdert DELETE gebeurtenissen voor de component Comments uit de activiteitsstroom.

### Pseudo-code voor EventListener {#pseudo-code-for-eventlistener}

Vereist het [nieuwste functiepakket](deploy-communities.md#latestfeaturepack).

```java
package my.company.comments;

import java.util.Collections;
import java.util.Map;

import org.apache.commons.lang.StringUtils;
import org.apache.felix.scr.annotations.Activate;
import org.apache.felix.scr.annotations.Component;
import org.apache.felix.scr.annotations.Modified;
import org.apache.felix.scr.annotations.Property;
import org.apache.felix.scr.annotations.Service;
import org.apache.sling.api.resource.Resource;
import org.apache.sling.commons.osgi.PropertiesUtil;
import org.osgi.service.component.ComponentContext;

import com.adobe.cq.social.activitystreams.listener.api.ActivityStreamProviderExtension;
import com.adobe.cq.social.commons.events.CommentEvent.CommentActions;
import com.adobe.cq.social.scf.core.SocialEvent;

@Service
@Component(metatype = true, label = "My Comment Delete Event Filter",
        description = "Prevents comment DELETE events from showing up in activity streams")
public class CommentDeleteEventActivityFilter implements ActivityStreamProviderExtension {

    @Property(name = "ranking", intValue = 10)
    protected int ranking;

    @Activate
    public void activate(final ComponentContext ctx) {
        ranking = PropertiesUtil.toInteger(ctx.getProperties().get("ranking"), 10);
    }

    @Modified
    public void update(final Map<String, Object> props) {
        ranking = PropertiesUtil.toInteger(props.get("ranking"), 10);
    }

    @Override
    public boolean evaluate(final SocialEvent<?> evt, final Resource resource) {
        if (evt.getAction() != null && evt.getAction() instanceof SocialEvent.SocialActions) {
            final SocialEvent.SocialActions action = evt.getAction();
            if (StringUtils.equals(action.getVerb(), CommentActions.DELETED.getVerb())) {
                return false;
            }
        }
        return true;
    }

    @Override
    public Map<String, ? extends Object> getActivityProperties(final SocialEvent<?> arg0, final Resource arg1) {
        return Collections.<String, Object>emptyMap();
    }

    @Override
    public Map<String, ? extends Object> getActorProperties(final SocialEvent<?> arg0, final Resource arg1) {
        return Collections.<String, Object>emptyMap();
    }

    @Override
    public String getName() {
        return "My Comment Delete Event Filter";
    }

    @Override
    public Map<String, ? extends Object> getObjectProperties(final SocialEvent<?> arg0, final Resource arg1) {
        return Collections.<String, Object>emptyMap();
    }

    /* Ensure a custom extension is registered with a ranking lower than any existing implementation in the product. */
    @Override
    public int getRanking() {
        return this.ranking;
    }

    @Override
    public Map<String, ? extends Object> getTargetProperties(final SocialEvent<?> arg0, final Resource arg1) {
        return Collections.<String, Object>emptyMap();
    }

    @Override
    public String[] getStreamProviderPid() {
        return new String[]{"*"};
    }

}
```

