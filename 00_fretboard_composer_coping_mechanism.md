# I Built a Music Composition Tool in Three Weeks to Learn A Song

...and now I can't really finish it until I learn to read music 

Fretboard Composer Pro: https://fretboard-composer-pro-330354285234.us-west1.run.app/

I've had an off-and-on love for guitar for over twelve years.

For the last five, I threw myself into DevOps and cloud systems administration instead: tiny apartments, AWS tutorials on double speed, chasing certifications, and babysitting fleets of Linux boxes and managed services. My world was terminals, networks, and infrastructure-as-code. I'd never touched front-end work in any serious way. My guitar sat in the corner, quietly gathering dust while I debugged Terraform plans and CI pipelines.

I had just made a big commitment: finish my degree at WGU, do a multicloud bootcamp, build ten production quality devops portfolio projects, and finish a 100 days of code challenge all at the same time over the course of this year.

Then a few months ago my life cracked open. I lost my best friend overnight when she simply stopped talking to me. Old childhood trauma started bubbling up in flashbacks. I came out as transgender. In the middle of all that, something beautiful happened too: I married a woman I love, who plays bass in the church band.

After that, bootcamps and portfolio projects suddenly felt flat. I kept asking myself, even if I got the DevOps job I was aiming at, what exactly was I going to do with all those skills? Who was I building for?

Spending time with my wife, picking the guitar back up, and tinkering with AI became my lifeline. I couldn't afford therapy. I quietly stopped doing cloud projects, deprioritzed school, read a stack of books on trauma, and decided to perform at open mic at my favorite bar.

## The problem: twelve years of guitar, zero repertoire

When I decided I wanted to play open mic, I hit a stupidly embarrassing wall: I'd been playing for around twelve years and I didn't really "know" any songs.

I could improvise, noodle, and follow chords by ear. (I learned guitar by going through a book of chords and scales.) But I couldn't pick up a piece of notation and just play it. The song I cared about learning properly was Jeff Buckley's "Lover, You Should've Come Over." It's full of extended voicings, voice-leading, and rhythmic nuance. The tab exists, sure, but I wanted to understand the timing that gave the song such an expressive feel.

That meant I had to finally learn to read music in a real way.

So now I had an interesting obstacle: to get on stage with the song I loved, I needed to bridge three gaps at once. I had to learn notation, map it to the fretboard in a way that made physical sense on my hands, and learn to sing.

This is where things got weird, and where my old skills came back around in a way I didn't expect.

## Letting go of "proper" software development

Up to this point, my software life was almost entirely back-end and infra. Bash, Python glue, Terraform, Kubernetes, IAM policies, log pipelines, that kind of thing. I knew just enough JavaScript to be dangerous in a browser console, but I'd never built a real front-end app, never mind anything with React, TypeScript, or canvas rendering.

Instead of spinning up another "serious" project that played to my strengths, I opened Google AI Studio, took a deep breath, and did everything you're not supposed to do.

I abandoned clean architecture. I abandoned planning. No TDD. No CI. No linters or static analysis tools or pre-commit or SonarQube. I stopped trying to impress some imaginary hiring manager. I just started prompting for code and seeing what happened.

I would describe a little piece of what I wanted - a fretboard where I could click fret positions and see them appear as notes in sheet music, a way to represent tunings and positions, the shape of a type that actually matches how guitarists think instead of abstract pitches. And then the model would spit out 500 lines of crap that did something completely different.

Around the same time, outside of code, I was neck-deep in books about trauma and Nonviolent Communication, trying to understand what had happened with my friend and how to talk to people without trampling their nervous systems. I was practicing this pattern of slowing down, naming what I was actually observing, what I was feeling, and what I needed, instead of just reacting.

Somewhere between those two worlds, a lightbulb went on: what if I talked to the LLM the way these therapy books and NVC folks were teaching me to talk to humans?

So I started coaching the model like it was a friend in distress. I would ask: What are your needs? Can you explain your understanding of the problem to me? What are your constraints? When I see foo, I feel bar because I need baz; can you help me foobar? What got in the way of you doing foo on your end? How did you come to the conclusion you did?

It sounds ridiculous, but it worked. The more I treated the LLM like something I could be in dialogue with - gently, clearly, with actual curiosity - the better its answers got. And, quietly, the more reps I got at using those same skills on myself. 

I think the only reason I was able to do this was because I've seen a lot of architectural issues over time. I taught myself functional programming in Haskell, which had some similarity to TypeScript. I've read about software patterns. I could say: you're introducing too many specialized types, reduce monomorphization with type clasess. Or, instead of using conditionals and properties, create an algebraic data type and pattern match. Or: what about this weird edge cases here? How are you going to persist the state? Try to follow a "functional core, imperative shell" pattern here.

Three weeks later, I had something that looked suspiciously like a professional composition tool. It was also, somehow, my first real front-end app.

It wasn't pretty from a software quality point of view, but the architecture was surprisingly not horrible, and it solved my very specific problem frighteningly well.

And because this isn't just a thought experiment: you can actually try it in your browser here -
Fretboard Composer Pro: https://fretboard-composer-pro-330354285234.us-west1.run.app/

## What I ended up building

The app is called Fretboard Composer Pro. On the surface, it's "just" a React + TypeScript app with a big canvas and some panels. Under the hood, it's an opinionated little lab for learning music notation from the vantage point of the guitar.

There's an interactive fretboard that actually understands the physics of playing. It doesn't just know that a C exists at a certain fret; it knows about strings, positions, and hand spans. When it generates a chord voicing, it scores it based on how ergonomic it is to play, not just whether the right pitches are present.

Beside that sits a standard music notation editor and a little piano roll. Everything is synced: click on the staff and you see all the places those notes can live on the fretboard; click on the fretboard and the notation updates. Change tunings or swap between six-string, seven-string, and bass setups, and the whole system adjusts.

On top of that core, I layered some tools for the version of me who's trying to learn "real" music, not just shapes.

There's a voicing engine that can search the neck for chord shapes inside a particular box, or prioritize certain intervals. There's a scale and exercise generator that can spit out fretboard runs and simple melodic ideas to practice in a given key. The audio side lets me feed in my voice or instrument so I can practice singing pitches and see them land inside the same system I'm composing in-- it will suggest where to play it on the neck.

And then there's the AI layer, wired through Google Gemini. Instead of being a chatbot next to the app, the model gets a structured view of the score and the fretboard. It knows what notes exist where, what the time signature and tempo are, and which parts of the neck are in play. I can ask it for a smoother way to voice a chord progression in a specific region, or for a simple melodic idea that fits the harmony I've already written, and it responds by proposing concrete edits to the composition.

In other words, I built the tool I wished existed when I first picked up guitar: something that treats the staff, the fretboard, my hands, and the underlying theory as one connected object, instead of three different worlds.

## The strange feedback loop this created

Here's the twist I didn't see coming: I can't actually finish this app unless I become the musician it assumes I am.

Every time I add a feature, I run into the limits of my own musical literacy. When I improve the notation editor, I have to check whether the rhythms are displayed correctly. When I tweak the chord analysis, I need to be able to look at a cluster of notes and tell whether the label makes sense. When I wire up new exercises, I have to judge whether they are musically useful rather than just technically correct.

The only way to QA my own code is to learn the thing I've been avoiding for years: reading and thinking in notation, not just boxes on the neck.

At the same time, I'm using the app itself to learn. I load in the open-mic song as my reference material. I slow it way down, map the chords and melodies into the editor, watch how they fan out over the fretboard, experiment with alternate voicings, and let the AI suggest gentle variations. Practicing becomes a loop between my ears, my hands, and the little system I built.

And on the DevOps side, this is the first time a personal project has naturally demanded all the "boring" infrastructure I used to force into fake portfolio apps. If I want to feel comfortable sharing this with other people, I really do need tests, a better state model, a real CI pipeline, and a sane way to ship updates without breaking people's work.

The difference is that now all of that serves a concrete, lived problem in my life: getting up on stage with a song I care about and not falling apart halfway through.

## Where this leaves me

I started this whole thing because I wanted to play one song at an open mic.

In the process, I ended up building an AI-powered composition environment, re-discovering my love of guitar, and accidentally giving myself a curriculum that ties together trauma recovery, gender, marriage, music, and DevOps.

Right now the app is in a funny limbo. Technically, it mostly works. It does everything I need it to to learn my song. But, emotionally, I'm not ready to call it "done" or to put a big GitHub link at the top of a post like this. The biggest missing piece isn't a feature; it's my own fluency.

But that's also what makes it feel alive. To finish the app, I have to become the kind of musician who can really use it. To become that musician, I get to lean on the app I've already built.

If there's a moral here, it's probably this: building something for your own very specific, slightly messy life can be more powerful than chasing a generic "portfolio-ready" idea. The feedback loop is brutal and honest. When the code is wrong, the guitar feels wrong. When the design is off, your hands tell you long before your linters do.

I don't know yet whether this project will turn into a portfolio project that will land me a job, or just make it easier to play Buckley at open mic, or just sing church songs in tune with my wife. But either way, it finally feels like all those years of cloud sysadmin, DevOps tutorials, and half-hearted guitar practice are pointing in the same direction.

And the bartenders who moonlight as muscianas in Carrboro seem to like it, too. And, maybe, my experiment can help you read music. It's the only thing out there that acknowledges that you can play a pitch in up to 5 different places on the neck and actually suggests where to play it.

If you're curious, you can poke at the live app here: https://fretboard-composer-pro-330354285234.us-west1.run.app/
