The following is ~~a comprehensive~~ an incomplete list of games I've played on stream.

**Disclaimers:** Links to the Humble Store are affiliate links. I, and a local charity of my choice, will receive a cut for any purchases made through those links. All other sites are non-affiliate links. For the PlayStation store, links have been omitted due to being region-locked, but you can look things up on your local store. Games are added to this list when I remember to add them without consulting any developers of those games. Links are accurate as of the time I add the game to the list, and they may or may not be updated further. There may also be disclosures specific to individual games, such as those received for free.

**Corrections:** If information about a game I've included is incorrect (for example, store links), or if you've seen me play a game and it's not on this list, the best way to get it fixed would be to [submit a GitHub issue](https://github.com/StevenH237/nixill.net/).

**Ratings:** Are on a scale of - (didn't like), 0 (indifferent), or + (liked), where games I *really* like or dislike can get an extra + or -. The reviews are pretty much just my opinions, and I'm not sure to what degree I'd call them objective or unbiased.

{% for game in site.data.games %}
---

<div markdown="1" data-gamename="{{ game.name | slugify: "latin" }}" data-rating="{{ game.rating | default: 0 }}" data-firstDate="{{ game.firstStream | date: '%s'}}" data-lastDate="{{ game.lastStream | date: '%s'}}">

# {{ game.name }}
{% if game.lastStream %}{% if game.lastStream == game.firstStream %}- Streamed from {{ game.platform }} on {{ game.firstStream | date: '%Y %b %e' }}{% elsif game.continuous %}- Streamed from {{ game.platform }} from {{ game.firstStream | date: '%Y %b %e' }} to {{ game.lastStream | date: '%Y %b %e' }}{% else %}- Streamed from {{ game.platform }}; first on {{ game.firstStream | date: '%Y %b %e' }}; most recently on {{ game.lastStream | date: '%Y %b %e' }}{% endif %}{% else %}- Streamed from {{ game.platform }} since {{ game.firstStream | date: '%Y %b %e' }}{% endif %}
- My rating: {% case game.rating %}{% when -2 %}**--**{: style="color: #b42b42;" }{% when -1 %}**-**{: style="color: #b42b42;" }{% when 0 %}0{% when 1 %}**+**{: style="color: #42b42b;" }{% when 2 %}**++**{: style="color: #42b42b;" }{% endcase %}
{% if game.finished == true %}- Did I finish it: Yes
{% elsif game.finished == false %}- Did I finish it: No
{% elsif game.finished %}- Did I finish it: {{ game.finished }}
{% endif -%}
{% if game.url %}- Website: [{{ game.url | split: "/" | first }}//{{ game.url | split: "/" | slice: 2 }}/]({{ game.url }}){% endif %}
{% if game.purchase -%}{%- assign purchase = game.purchase -%}{%- assign slash = false -%}- Where to {% if purchase.free %}get{% else %}buy{% endif %}:
{% if purchase.humble.pc %} [**Humble Store ({{ purchase.humble.pcPlatform | default: "Steam" }})**](https://www.humblebundle.com/store/{{ purchase.humble.pc }}?partner=nixill&charity=1599605){%- assign slash = true -%}{%- endif -%}
{% if purchase.humble.nin10 %}{% if slash %} /{% endif %} [**Humble Store ({{ purchase.humble.nin10Platform | default: "Switch" }})**](https://www.humblebundle.com/store/{{ purchase.humble.nin10 }}?partner=nixill&charity=1599605){%- assign slash = true -%}{% endif -%}
{% if purchase.steam %}{% if slash %} /{% endif %} [Steam](https://store.steampowered.com/app/{{ purchase.steam }}){%- assign slash = true -%}{% endif -%}
{% if purchase.gog %}{% if slash %} /{% endif %} [GOG](https://www.gog.com/game/{{ purchase.gog }}){%- assign slash = true -%}{% endif -%}
{% if purchase.itch %}{% if slash %} /{% endif %} [itch.io](https://{{ purchase.itch.user }}.itch.io/{{ purchase.itch.game }}){%- assign slash = true -%}{% endif -%}
{% if purchase.nin10 %}{% if slash %} /{% endif %} [Nintendo eShop ({{ purchase.nin10.platform | default: "Switch" }})](https://www.nintendo.com/store/products/{{ purchase.nin10.link }}){%- assign slash = true -%}{% endif -%}
{% if purchase.ps %}{% if slash %} /{% endif %} PlayStation ({{ purchase.ps }}){%- assign slash = true -%}{% endif -%}
{% if purchase.xbox %}{% if slash %} /{% endif %} [Xbox ({{ purchase.xbox.platform | default: "One/Series X\|S" }})](https://www.xbox.com/games/store/{{ purchase.xbox.link }}){%- assign slash = true -%}{% endif -%}
{% if purchase.ios %}{% if slash %} /{% endif %} [iOS](https://apps.apple.com/app/{{ purchase.ios }}){%- assign slash = true -%}{% endif -%}
{% if purchase.android %}{% if slash %} /{% endif %} [Android](https://play.google.com/store/apps/details?id={{ purchase.android }}){%- assign slash = true -%}{% endif -%}
{% if purchase.other %}{% if slash %} /{% endif %} [{{ purchase.other.name }}]({{ purchase.other.link }}){%- assign slash = true -%}{% endif -%}{% endif %}

{% if game.disclosures %}**Disclosures:** {% if game.disclosures.humble %}*Humble:* I received this game as part of a Humble Monthly subscription or a Humble Bundle, without having spent any money with the explicit intent of getting it. {% endif %}{{ game.disclosures.text }}{% endif %}

{% if game.notes %}**Notes:** {{ game.notes }}{% endif %}

{% if game.review %}### My review:

{% if game.review.plus %}**The good:** {{ game.review.plus }}

**The bad:** {{ game.review.minus }}{% endif %}

{% if game.review.more %}**More:** {{ game.review.more }}{% endif %}{% endif %}

</div>

{%- endfor -%}