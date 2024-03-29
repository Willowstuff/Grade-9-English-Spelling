<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Spelling Test</title>
    <style>
        body {
            font-family: Arial, sans-serif;
            background-color: #f2f2f2;
            margin: 0;
            padding: 0;
            display: flex;
            justify-content: center;
            align-items: center;
            height: 100vh;
        }
        .container {
            background-color: #fff;
            padding: 20px;
            border-radius: 8px;
            box-shadow: 0 2px 5px rgba(0, 0, 0, 0.1);
            max-width: 400px;
            width: 100%;
            text-align: center;
        }
        h1 {
            color: #333;
            margin-top: 0;
        }
        p {
            color: #555;
        }
        button {
            background-color: #4CAF50;
            color: white;
            padding: 10px 20px;
            border: none;
            border-radius: 4px;
            cursor: pointer;
            margin-top: 10px;
            margin-right: 10px;
            transition: background-color 0.3s;
        }
        button:hover {
            background-color: #45a049;
        }
        input[type="text"] {
            padding: 10px;
            border: 1px solid #ccc;
            border-radius: 4px;
            width: 60%;
            margin-top: 10px;
            box-sizing: border-box;
        }
        label {
            display: block;
            text-align: left;
            color: #333;
            margin-top: 10px;
        }
    </style>
    <script>
        const words = [
    "absence", "accommodate", "achieve", "acquire", "across", "address", "advertise", "advice", "among", "apparent",
    "argument", "athlete", "awful", "balance", "basically", "beautiful", "because", "becoming", "before", "beginning",
    "believe", "benefit", "breathe", "brilliant", "business", "calendar", "careful", "category", "ceiling", "cemetery",
    "abbreviate", "absurd", "abundance", "accidentally", "accompanying", "according", "acknowledge", "acquit", "aeroplane",
    "aggravate", "affect", "aggression", "alcohol", "allege", "allot", "amateur", "arithmetic", "bachelor", "balloon",
    "bankruptcy", "barbarous", "barbecue", "bicycle", "biscuit", "bureau", "belief", "burglar", "calm", "acrobat",
    "acrophobia", "amble", "ambulant", "ambulance", "amiable", "amity", "amorous", "anthology", "anthozoan", "aphorism",
    "apology", "apostrophe", "audience", "auditorium", "antipathy", "combine", "contact", "collect", "co-worker",
    "degenerate", "disappear", "disapprove", "dishonest", "distant", "dislike", "endeavour", "empathise", "epitaph",
    "epilogue", "certain", "chief", "citizen", "coming", "competition", "convenience", "criticise", "decide", "definite",
    "deposit", "describe", "desperate", "develop", "difference", "dilemma", "disappear", "disappoint", "discipline",
    "does", "during", "easily", "eight", "either", "embarrass", "environment", "equipped", "exaggerate", "excellent",
    "except", "exercise", "existence", "expect", "experience", "experiment", "explanation", "familiar", "fascinating",
    "finally", "foreign", "forty", "forward", "friend", "campaign", "chaos", "casualties", "celebrity", "cellophane",
    "chili", "concede", "calendar", "camouflage", "changeable", "collectible", "colonel", "column", "committed", "committee",
    "conscience", "conscientious", "conscious", "consensus", "controversy", "coolly", "commitment", "dealt", "debater",
    "debt", "decaffeinated", "decathlon", "defendant", "descend", "desirable", "doubt", "disease", "discreet", "disastrous",
    "deceive", "desert", "dessert", "deterrence", "discipline", "definitely", "dependent", "echoes", "brewed", "brood",
    "bridal", "bridle", "broach", "brooch", "carat", "carrot", "karat", "census", "senses", "choral", "coral", "chord",
    "cord", "cored", "colonel", "kernel", "discussed", "disgust", "elicit", "illicit", "elude", "allude", "illude",
    "barometer", "baritone", "candid", "incandescent", "cardiac", "cardiologist", "carnivorous", "incarnate", "energy",
    "surgeon", "jury", "jurisdiction", "pathetic", "describe", "prescription", "insomnia", "somnolent", "consonant",
    "supersonic", "unison", "philosopher", "sophisticated", "sophism", "biosphere", "hemisphere", "inspire", "transpire",
    "spirit", "constellation", "interstellar", "terminate", "determine", "exterminate", "contortion", "retort", "proceed",
    "promote", "regenerate", "secede", "seclude", "semifinal", "submission", "supersede", "transformation", "transcontinental",
    "transverse", "uncouth", "undercarriage", "comfortable", "performance", "truancy", "necessary", "neighbour", "neither",
    "noticeable", "occasion", "occurred", "official", "often", "omission", "operate", "optimism", "original", "ought", "paid",
    "parallel", "particularly", "peculiar", "perceive", "perform", "permanent", "persevere", "personally", "persuade", "picture",
    "piece", "planning", "pleasant", "political", "possess", "possible", "practical", "prefer", "prejudice", "presence", "privilege",
    "probably", "professional", "promise", "proof", "psychology", "quantity", "quarter", "indispensable", "innocent", "inoculate",
    "itinerary", "jealousy", "jewellery", "khaki", "kindergarten", "kernel", "language", "lasagne", "legible", "likable", "liquefy",
    "luxurious", "laugh", "liaise", "licence", "lieutenant", "loose", "lose", "leisure", "lightning", "loneliness", "magical",
    "magnificent", "maintain", "manual", "matinee", "mediocre", "millennium", "millionaire", "miscellaneous", "monastery", "murmur",
    "marshmallow", "medieval", "memento", "mischievous", "misspell", "mnemonic", "jamb", "jewel", "joule", "lumbar", "lumber",
    "maize", "maze", "mall", "maul", "manner", "manor", "medal", "meddle", "mews", "muse", "pair", "pare", "pear", "palate", "pallet",
    "palette", "patience", "patients", "pause", "paws", "detoxification", "toxicology", "intoxicated", "vocal", "vocabulary",
    "provide", "vision", "hopped", "wooden", "higher", "occupant", "respondent", "teacher", "actor", "biggest", "careful", "linguistic",
    "running", "occasion", "attraction", "infinity", "unity", "plaintive", "quiet", "quit", "quite", "realise", "receive", "recognise",
    "recommend", "reference", "religious", "repetition", "restaurant", "rhythm", "ridiculous", "sacrifice", "safety", "scissors",
    "secretary", "separate", "shining", "similar", "sincerely", "soldier", "speech", "stopping", "strength", "studying", "succeed",
    "successful", "surely", "surprise", "temperature", "temporary", "through", "through", "toward", "tries", "truly", "twelfth", "until",
    "unusual", "using", "usually", "maintenance", "manoeuvre", "naturally", "negotiable", "naïve", "necessary", "obedience", "oneself",
    "opportunity", "overrun", "occasion", "occur", "outrageous", "pamphlet", "paralyse", "parliament", "patience", "penitentiary",
    "personnel", "phenomenon", "pneumonia", "prejudice", "pastime", "playwright", "possession", "potassium", "potato", "practice",
    "principal", "proceed", "professor", "pronunciation", "pursue", "quarantine", "quantity", "queue", "questionnaire", "receipt",
    "reign", "relieve", "renaissance", "rescind", "peak", "peek", "pique", "peal", "peel", "pedal", "peddle", "peer", "pier", "pistil",
    "pistol", "plum", "plumb", "presents", "presence", "pride", "pryed", "pries", "prize", "prince", "prints", "raise", "rays", "raze",
    "ray", "wrap", "fearless", "quickly", "zoology", "anthropology", "enjoyment", "kindness", "joyous", "books", "boxes", "aptitude",
    "happy", "village", "weird", "welcome", "whether", "writing", "reservoir", "roommate", "relevant", "supersede", "sandal", "sandwich",
    "savvy", "siege", "seize", "shepherd", "sheriff", "subtly", "schedule", "sergeant", "tomato", "tomorrow", "tyranny", "tangible",
    "technique", "tenacious", "tongue", "triathlon", "tragedy", "unfortunately", "ukulele", "unanimous", "usage", "undoubtedly",
    "vacuum", "valuable", "vilify", "vicious", "warfare", "wilful", "xylophone", "yacht", "real", "reel", "recede", "reseed", "review",
    "revue", "rigger", "rigor", "rye", "wry", "sail", "sale", "sane", "seine", "scene", "seen", "scull", "skull", "slay", "sleigh",
    "soar", "sore", "soared", "sword", "suede", "swayed", "sundae", "Sunday", "tare", "tear", "taught", "taut", "team", "teem", "tear",
    "tier", "troop", "troup", "trussed", "trust", "vain", "wane", "vein", "verses", "versus", "wade", "weighed", "wail", "wale", "whale"
];


        const definitions = [
    "the state of being away", "provide lodging or sufficient space for", "successfully bring about or reach", 
    "buy or obtain (an asset or object) for oneself", "from one side to the other", "the particulars of the place where someone lives or an organization is situated", 
    "describe or draw attention to (a product, service, or event) in a public medium in order to promote sales or attendance", 
    "guidance or recommendations offered with regard to prudent future action", "surrounded by; in the midst of", "clearly visible or understood; obvious", 
    "an exchange of diverging or opposite views, typically a heated or angry one", "a person who is proficient in sports and other forms of physical exercise", 
    "very bad or unpleasant", "an even distribution of weight ensuring stability", "in essence; at heart", "pleasing the senses or mind aesthetically", 
    "for the reason that; since", "begin to be; come to be", "during the period of time preceding (a particular event or time)", 
    "the point in time or space at which something begins", "accept that (something) is true, especially without proof", 
    "an advantage or profit gained from something", "take air, liquid, or another substance into the lungs and then expel it, especially as a regular physiological process", 
    "exceptionally clever or talented", "the practice of making one's living by engaging in commerce", "a chart or series of pages showing the days, weeks, and months of a particular year", 
    "exercising or taking care to avoid potential danger or difficulties", "a class or division of people or things regarded as having particular shared characteristics", 
    "the upper interior surface of a room or other similar compartment", "a burial ground; a cemetery", "make (something) shorter", 
    "wildly unreasonable, illogical, or inappropriate", "a very large quantity of something", "by accident; unintentionally", 
    "present with at the same time; accompany", "as stated or indicated by; on the authority of", "accept or admit the existence or truth of", 
    "free (someone) from a criminal charge by a verdict of not guilty", "a powered flying vehicle with fixed wings and a weight greater than that of the air it displaces", 
    "make (a problem, injury, or offense) worse or more serious", "have an effect on; make a difference to", "feel or show aggression or hostility towards", 
    "a colorless volatile flammable liquid that is the intoxicating constituent of wine, beer, spirits, and other drinks", 
    "claim or assert that someone has done something illegal or wrong, typically without evidence", "a great deal", 
    "give or apportion (something) to someone as a share or task", "a person who engages in a pursuit, especially a sport, on an unpaid basis", 
    "the branch of mathematics dealing with the properties and manipulation of numbers", "a bachelor's degree", 
    "a small rubber bag filled with air or gas, used as a child's toy or a decoration", "the state of being bankrupt", 
    "savagely cruel; exceedingly brutal", "cook (meat, fish, or other food) on a barbecue", "a vehicle composed of two wheels held in a frame one behind the other, propelled by pedals and steered with handlebars attached to the front wheel", 
    "a small baked unleavened cake, typically crisp, flat, and sweet", "a writing desk with drawers and typically an angled top opening downward to form a writing surface", 
    "trust, faith, or confidence in someone or something", "a person who commits burglary", "calm; not showing or feeling nervousness, anger, or other strong emotions", 
    "a performer of gymnastic feats, especially when suspended by the hands or the feet", "an extreme or irrational fear of heights", 
    "walk or move at a slow, relaxed pace", "relating to or adapted for walking", "a vehicle equipped for taking sick or injured people to and from the hospital, especially in emergencies", 
    "having or displaying a friendly and pleasant manner", "a friendly relationship", "showing, feeling, or relating to sexual desire", 
    "a published collection of poems or other pieces of writing", "a class of marine animals that includes corals and sea anemones", 
    "a pithy observation that contains a general truth", "a regretful acknowledgment of an offense or failure", 
    "a punctuation mark (') used to indicate either possession (e.g., Harry's book) or the omission of letters or numbers", 
    "the assembled spectators or listeners at a public event, such as a play, movie, concert, or meeting", 
    "the part of a theater, concert hall, or other area where the audience sits", "a deep-seated feeling of dislike; aversion", 
    "bring together or into contact so that a real or notional link is established", "bring or gather together (a number of things)", 
    "a person with whom one works, especially in a profession or business", "having lost the physical, mental, or moral qualities considered normal and desirable; showing evidence of decline", 
    "cease to be visible", "have a view or judgment about", "deceitful or fraudulent; disposed to cheat or defraud", 
    "not near or far in space", "feel distaste for or hostility toward", "try hard to do or achieve something", "showing a hopeless sense that a situation is so bad as to be impossible to deal with", 
    "create or evolve (something) from a simple or complex system of processes", "a point or way in which people or things are not the same", 
    "a situation in which a difficult choice has to be made between two or more alternatives, especially equally undesirable ones", 
    "cease to be visible", "fail to meet the hopes or expectations of", "the practice of training people to obey rules or a code of behavior, using punishment to correct disobedience", 
    "perform (an act, duty, or role) as part of one's employment or position", "perform (an activity) or exercise (a skill) repeatedly or regularly in order to improve or maintain one's proficiency", 
    "having a specified position in space", "describe the qualities or peculiarities of", "extremely severe", "having lost all hope; despairing", 
    "grow or cause to grow and become more mature, advanced, or elaborate", "a point or way in which people or things are not the same", 
    "a quality or feature regarded as a characteristic or inherent part of someone or something", "draw a distinction between; perceive or point out a difference", 
    "a matter of life and death; very serious", "having a great ability to learn or understand things, or to deal with new or difficult situations", 
    "arousing great interest or curiosity", "interrupt (someone) while speaking", "cease to feel angry or bitter towards (someone)", 
    "adhering firmly to something; refusing to give up", "marked by humor; funny", "the state of being happy", 
    "a person who is admired or idealized for courage, outstanding achievements, or noble qualities", "causing laughter or amusement; funny", 
    "the fact of being oneself; selfhood", "the fact or condition of being regarded or treated as more important", 
    "an act of kindness, such as making a donation or doing a favor", "enjoyment, amusement, or lighthearted pleasure", 
    "a feeling of great pleasure and happiness", "printed or written works, especially those considered of superior or lasting artistic merit", 
    "a container with a flat base and sides, typically square or rectangular and having a lid", "a natural ability to do something", 
    "feeling or showing pleasure or contentment", "feeling or showing a cheerful willingness to do favors for others", "the state or quality of being happy", 
    "a group of houses and associated buildings, larger than a hamlet and smaller than a town, situated in a rural area", 
    "suggesting something supernatural; uncanny", "an instance or manner of greeting someone", 
    "expressing a doubt or choice between alternatives", "the activity or skill of writing", "a large natural or artificial lake used as a source of water supply", 
    "a person occupying the same room as another", "closely connected or appropriate to what is being done or considered", 
    "take the place of (a person or thing) in a position of authority or significance", "a light shoe with either an openwork upper or straps attaching the sole to the foot", 
    "an item of food consisting of two pieces of bread with a filling between them, eaten as a light meal", "shrewdness and practical knowledge, especially in politics or business", 
    "a military operation in which enemy forces surround a town or building, cutting off essential supplies, with the aim of compelling those inside to surrender", 
    "take hold of suddenly and forcibly", "a person who tends and rears sheep", "a sheriff's officer who oversees the county jail and its prisoners", 
    "in a way that is so delicate or precise as to be difficult to analyze or describe", "a plan for carrying out a process or procedure, giving lists of intended events and times", 
    "a rank of noncommissioned military officers above corporal and below staff sergeant in the army or marines", 
    "a glossy red, or occasionally yellow, pulpy edible fruit which is eaten as a vegetable or in salad", "the day following today", 
    "cruel and oppressive government or rule", "perceptible by touch or apparently so; tangible", "a way of carrying out a particular task, especially the execution or performance of an artistic work or a scientific procedure", 
    "tending to keep a firm hold of something; clinging or adhering closely", "the fleshy muscular organ in the mouth of a mammal, used for tasting, licking, swallowing, and (in humans) articulating speech", 
    "an athletic contest consisting of three different events, typically swimming, cycling, and long-distance running", 
    "an event causing great suffering, destruction, and distress, such as a serious accident, crime, or natural catastrophe", 
    "used to indicate a situation in which one event is causing another to happen", "a small guitar with four strings, typically plucked with the thumb and index fingers", 
    "agreed upon or shared by all parties", "the action of using something or the fact of being used", 
    "used to indicate that one is unsure about the truth or accuracy of something", "a device generating suction or capable of maintaining a partial vacuum", 
    "having a great deal of money or assets; very valuable or useful", "speak or write about in an abusively disparaging manner", 
    "deliberately cruel or violent", "engagement in or the activities involved in war or conflict", "having or showing a stubborn and determined intention to do as one wants, regardless of the consequences", 
    "a musical instrument consisting of a graduated series of wooden bars, played by striking with mallets", "a medium-sized sailboat with a fore-and-aft rig",
    "having objective independent existence", "wind onto a reel", "move back or away, especially because of fear or disgust", 
    "sow (seed) again", "a formal assessment or examination of something with the possibility or intention of instituting change if necessary", 
    "a light entertainment consisting of a series of short sketches, songs, and dances, typically dealing satirically with topical issues", 
    "a person who rigs", "stiffness of a corpse or an animal in rigor mortis", "a cereal plant that tolerates poor soils and low temperatures", 
    "using or expressing dry, especially mocking, humor", "move (a boat) using a seine", "the place where an incident in real life or fiction occurs or occurred", 
    "past and past participle of 'see'", "a small boat used in or adapted for rowing", "the bone structure of the head; cranium", 
    "kill (a person or animal) in a violent way", "a sled drawn by horses or reindeer, especially one used for passengers", 
    "fly or rise high in the air", "painful or aching", "fly or rise high in the air", "move upward quickly or suddenly", 
    "a weapon with a long metal blade and a hilt with a handguard, used for thrusting or striking and now typically worn as part of ceremonial dress", 
    "a type of soft leather, made from the underside of the skin", "move or cause to move slowly or rhythmically backward and forward or from side to side", 
    "a dish of ice cream with added ingredients such as syrup, fruit, or nuts", "the first day of the week, observed as a day of rest and worship by most Christians", 
    "a deduction from the gross weight to allow for the weight of packaging", "pull or rip (something) apart or to pieces with force", 
    "stretched or pulled tight; not slack", "two or more people working together", "be full of or swarming with", 
    "be full of or swarming with", "a drop of the clear salty liquid secreted by glands in a person's eye when they cry or when the eye is irritated", 
    "a row or level of a structure, typically one of a series of rows placed one above the other and successively receding or diminishing in size", 
    "a group of soldiers, especially a cavalry unit commanded by a captain, or an airborne unit", 
    "a group of actors, dancers, or other entertainers who tour to different venues", 
    "a person who sells goods, especially illegally or dishonestly", "firm belief in the reliability, truth, ability, or strength of someone or something", 
    "lose strength or effectiveness; become weak", "a blood vessel carrying blood towards the heart", 
    "lines of words that appear together on a page and have a similar form but are not part of a poem", 
    "expressing opposition or resistance; against", "walk with effort through water or another liquid or viscous substance", 
    "find out the weight of", "a prolonged high-pitched cry of pain, grief, or anger", "a raised ridge in knitted fabric", 
    "a very large marine mammal with a streamlined hairless body, a horizontal tail fin, and a blowhole on top of its head for breathing", 
    // Continue with the remaining definitions...
];


        let currentWordIndex = 0;

        function startTest() {
            readWord();
            document.getElementById('inputBox').focus();
        }

        function readWord() {
            const word = words[currentWordIndex];
            const definition = definitions[currentWordIndex];
            const speech = new SpeechSynthesisUtterance();
            speech.text = word;
            window.speechSynthesis.speak(speech);
            alert(definition); // Display the definition as an alert
        }

        function repeatWord() {
            readWord();
        }

        function checkSpelling() {
            const input = document.getElementById('inputBox').value.trim().toLowerCase();
            const word = words[currentWordIndex].toLowerCase();
            if (input === word) {
                alert("Correct!");
            } else {
                alert("Incorrect. The correct spelling is: " + word);
            }
            currentWordIndex++;
            if (currentWordIndex < words.length) {
                readWord();
                document.getElementById('inputBox').value = "";
            } else {
                alert("Test finished!");
            }
        }
    </script>
</head>
<body>
    <div class="container">
        <h1>Spelling Test</h1>
        <p>Listen to the word and spell it correctly:</p>
        <button onclick="startTest()">Start Test</button>
        <button onclick="repeatWord()">Repeat Word</button>
        <div>
            <label for="inputBox">Your spelling:</label>
            <input type="text" id="inputBox">
            <button onclick="checkSpelling()">Check</button>
        </div>
    </div>
</body>
</html>
