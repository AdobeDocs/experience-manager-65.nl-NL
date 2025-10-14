---
title: OSGi Events for Communities Components
description: OSGi-gebeurtenissen worden verzonden die asynchrone listeners kunnen activeren
contentOwner: msm-service
products: SG_EXPERIENCEMANAGER/6.5/COMMUNITIES
topic-tags: developing
content-type: reference
exl-id: 8049d797-e758-44c2-a89b-51d2b2fca8dc
solution: Experience Manager
feature: Communities
role: Admin
source-git-commit: 1f56c99980846400cfde8fa4e9a55e885bc2258d
workflow-type: tm+mt
source-wordcount: '592'
ht-degree: 0%

---

# OSGi Events for Communities Components  {#osgi-events-for-communities-components}

## Overzicht {#overview}

Wanneer leden met de eigenschappen van de Gemeenschappen in wisselwerking staan, worden de gebeurtenissen OSGi verzonden die asynchrone luisteraars, zoals berichten of gamificatie (het scoren en het merken) kunnen teweegbrengen.

De instantie van een component [&#x200B; SocialEvent &#x200B;](https://helpx.adobe.com/experience-manager/6-5/sites/developing/using/reference-materials/javadoc/com/adobe/cq/social/scf/core/SocialEvent.html) registreert de gebeurtenissen als `actions` die voor a `topic` voorkomen. De SocialEvent bevat een methode om een `verb` te retourneren die aan de handeling is gekoppeld. Er is een *n-1* verhouding tussen `actions` en `verbs`.

Voor de Community-componenten die in de release worden geleverd, worden in de volgende tabellen de `verbs` gedefinieerd voor elke `topic` die beschikbaar is voor gebruik.

## Onderwerpen en werven {#topics-and-verbs}

[&#x200B; Component van de Kalender &#x200B;](calendar-basics-for-developers.md)
SocialEvent `topic`= com/adobe/cq/social/agenda

| **Verb** | **Beschrijving** |
|---|---|
| POST | Lid maakt een kalendergebeurtenis |
| ADD | Opmerkingen van de lidstaten over een kalendergebeurtenis |
| BIJWERKEN | De agendagebeurtenis of de opmerking van het lid wordt bewerkt |
| DELETE | De agendagebeurtenis of de opmerking van het lid wordt verwijderd |

[&#x200B; Component van Commentaren &#x200B;](essentials-comments.md)
SocialEvent `topic`= com/adobe/cq/social/comment

| **Verb** | **Beschrijving** |
|---|---|
| POST | Lid maakt een opmerking |
| ADD | Antwoorden van de lidstaten op opmerkingen |
| BIJWERKEN | Opmerking van lid wordt bewerkt |
| DELETE | Opmerking van lid wordt verwijderd |

[&#x200B; de Component van de Bibliotheek van het Dossier &#x200B;](essentials-file-library.md)
SocialEvent `topic`= com/adobe/cq/social/fileLibrary

| **Verb** | **Beschrijving** |
|---|---|
| POST | Lid maakt een map |
| ATTACH | Lid uploadt een bestand |
| BIJWERKEN | Lid werkt een omslag of een dossier bij |
| DELETE | Lid verwijdert een map of bestand |

[&#x200B; Component van het Forum &#x200B;](essentials-forum.md)
SocialEvent `topic`= com/adobe/cq/social/forum

| **Verb** | **Beschrijving** |
|---|---|
| POST | Lid maakt het forum |
| ADD | Antwoorden van de lidstaten op het forum |
| BIJWERKEN | Het onderwerp of antwoord van het forum van het lid wordt bewerkt |
| DELETE | Het onderwerp of de reactie van het lid in het forum wordt geschrapt |

[&#x200B; Component van het Dagboek &#x200B;](blog-developer-basics.md)
SocialEvent `topic`= com/adobe/cq/social/journaal

| **Verb** | **Beschrijving** |
|---|---|
| POST | Lid maakt een blogartikel |
| ADD | Opmerkingen van leden over blogartikelen |
| BIJWERKEN | Blogartikel of commentaar van lid wordt bewerkt |
| DELETE | Blogartikel of commentaar van lid wordt verwijderd |

[&#x200B; Component QnA &#x200B;](qna-essentials.md)
SocialEvent `topic` = com/adobe/cq/social/qna

| **Verb** | **Beschrijving** |
|---|---|
| POST | Lid maakt een QnA-vraag |
| ADD | Lid maakt een antwoord op vraag |
| BIJWERKEN | Vraag of antwoord van lid wordt bewerkt |
| SELECT | Antwoord van lid is geselecteerd |
| SELECTEREN OPHEFFEN | Het antwoord van het lid is niet geselecteerd |
| DELETE | Vraag of antwoord van lid wordt verwijderd |

[&#x200B; Component van Revisies &#x200B;](reviews-basics.md)
SocialEvent `topic`= com/adobe/cq/social/review

| **Verb** | **Beschrijving** |
|---|---|
| POST | Lid leidt tot herziening |
| BIJWERKEN | Revisie van lid wordt bewerkt |
| DELETE | Herziening door lid wordt verwijderd |

[&#x200B; de Component van de Classificatie &#x200B;](rating-basics.md)
SocialEvent `topic`= com/adobe/cq/social/tally

| **Verb** | **Beschrijving** |
|---|---|
| WAARDERING TOEVOEGEN | De inhoud van het lid is vervangen |
| RATING VERWIJDEREN | De inhoud van het lid is verlaagd |

[&#x200B; Stemende Component &#x200B;](essentials-voting.md)
SocialEvent `topic`= com/adobe/cq/social/tally

| **Verb** | **Beschrijving** |
|---|---|
| STEMMING TOEVOEGEN | Er is gestemd over de inhoud van het lid |
| STEMMING VERWIJDEREN | Over de inhoud van het lid is gestemd |

**moderatie-Toegelaten Componenten**
SocialEvent `topic`= com/adobe/cq/social/moderation

| **Verb** | **Beschrijving** |
|---|---|
| DENKEN | De inhoud van het lid wordt geweigerd |
| VLAG ALS ONJUIST | Inhoud van lid is gemarkeerd |
| ONGESCHIKTE LAG ALS ONJUIST | Inhoud van lid is niet gemarkeerd |
| ACCEPTEREN | De inhoud van het lid wordt goedgekeurd door moderator |
| SLUITEN | Lid sluit commentaar op bewerkingen en reacties |
| OPENEN | Opmerking voor opnieuw openen van lid |

## Gebeurtenissen voor aangepaste componenten {#events-for-custom-components}

Voor een douanecomponent, moet de [&#x200B; abstracte klasse SocialEvent &#x200B;](https://helpx.adobe.com/experience-manager/6-5/sites/developing/using/reference-materials/javadoc/com/adobe/cq/social/scf/core/SocialEvent.html) worden uitgebreid om de gebeurtenissen van de component te registreren zoals `actions` die voor a `topic` voorkomen.

De douanegebeurtenis zou de methode `getVerb()` met voeten treden zodat aangewezen `verb` voor elke `action` is teruggekeerd. De `verb` die voor een actie wordt geretourneerd, kan een algemene instructie zijn (zoals `POST` ) of een speciale instructie voor de component (zoals `ADD RATING` ). Er is een *n-1* verhouding tussen `actions` en `verbs`.

>[!NOTE]
>
>Zorg ervoor dat een aangepaste extensie is geregistreerd met een lagere rangschikking dan een bestaande implementatie in het product.

### Pseudo-code voor gebeurtenis Custom Component {#pseudo-code-for-custom-component-event}

[&#x200B; org.osgi.service.event.Event &#x200B;](https://osgi.org/javadoc/r4v41/org/osgi/service/event/Event.html);
[&#x200B; com.adobe.cq.social.scf.core.SocialEvent &#x200B;](https://helpx.adobe.com/experience-manager/6-5/sites/developing/using/reference-materials/javadoc/com/adobe/cq/social/scf/core/SocialEvent.html);
[&#x200B; com.adobe.granite.activity.streams.ObjectTypes &#x200B;](https://helpx.adobe.com/experience-manager/6-5/sites/developing/using/reference-materials/javadoc/com/adobe/granite/activitystreams/ObjectTypes.html);
[&#x200B; com.adobe.granite.activity streams.Verbs &#x200B;](https://helpx.adobe.com/experience-manager/6-5/sites/developing/using/reference-materials/javadoc/com/adobe/granite/activitystreams/Verbs.html);

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

In het volgende pseudo-codevoorbeeld worden DELETE-gebeurtenissen voor de component Comments verwijderd uit de activiteitsstroom.

### Pseudo-code voor EventListener {#pseudo-code-for-eventlistener}

Vereist [&#x200B; recentste eigenschappak &#x200B;](deploy-communities.md#latestfeaturepack).

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
