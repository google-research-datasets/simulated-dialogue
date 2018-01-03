# Simulated Dialogue

## About

These datasets consist of conversations between an agent and a user. These
conversations correspond to task oriented dialogues related to restaurants or
movies and are generated using a dialogue simulator. The simulator generates the
dialogue acts containing the act type and associated arguments for user and
system and the dialogue state for each turn of the conversation. Then,
crowdworkers are asked to generate natural language utterances corresponding to
each turn, given the dialogue acts.

The number of dialogues in each dataset are listed below:

| Dataset            | Slots                                                                          | Train | Dev | Test |
| ------------------ | ------------------------------------------------------------------------------ | ----- | --- | ---- |
| Sim-R (Restaurant) | price\_range, location, restaurant\_name,<br>category, num\_people, date, time | 1116  | 349 | 775  |
| Sim-M (Movie)      | theatre\_name, movie, date, time,<br>num\_people                               | 384   | 120 | 264  |

**The datasets are provided "AS IS" without any warranty, express or implied.
Google disclaims all liability for any damages, direct or indirect, resulting
from the use of these datasets.**

**Please email {abhirast, dilekh, pararth}@google.com with questions.**

## Structure of the Data

Each dialogue is represented as a json object with the following fields:

*   **dialogue\_id** - A unique identifier for a dialogue.
*   **turns** - A list of annotated agent and user utterance pairs having the
    following fields:
    *   **system\_acts** - A list of system actions. An action consists of an
        action type, and optional slot and value arguments. Each action has the
        following fields:
        *   **type** - An action type. Possible values are listed below.
        *   **slot** - Optional slot argument.
        *   **value** - Optional value argument. If value is present, slot must
            be present.
    *   **system\_utterance** - The system utterance having the following
        fields.
        *   **text** - The text of the utterance.
        *   **tokens** - A list containing tokenized version of text.
        *   **slots** - A list containing locations of mentions of values
            corresponding to slots in the utterance, having the following
            fields:
            *   **slot** - The name of the slot
            *   **start** - The index of the first token corresponding to a slot
                value in the tokens list.
            *   **exclusive\_end** - The index of the token succeeding the last
                token corresponding to the slot value in the tokens list. In
                python, `tokens[start:exclusive_end]` gives the tokens for slot
                value.
    *   **user\_acts** - A list of user actions. Has the same structure as
        system\_acts.
    *   **user\_utterance** - The user utterance. It has three fields, similar
        to system\_utterance.
    *   **user_intents** - A list of user intents specified in the current turn.
        Possible values are listed below.
    *   **dialogue\_state** - Contains the preferences for the different slots
        as specified by the user upto the current turn of the dialogue.
        Represented as a list containing:
        *   **slot** - The name of the slot.
        *   **value** - The value assigned to the slot.

The list of action types is inspired from the Cambridge dialogue act schema
([DSTC2 Handbook](http://camdial.org/~mh521/dstc/downloads/handbook.pdf), Pg 19)
. The possible values are:

*   AFFIRM
*   CANT\_UNDERSTAND
*   CONFIRM
*   INFORM
*   GOOD\_BYE
*   GREETING
*   NEGATE
*   OTHER
*   NOTIFY\_FAILURE
*   NOTIFY\_SUCCESS
*   OFFER
*   REQUEST
*   REQUEST\_ALTS
*   SELECT
*   THANK\_YOU

The possible values of user intents are:

*   BUY\_MOVIE\_TICKETS
*   FIND\_RESTAURANT
*   RESERVE\_RESTAURANT

## Dialogue State Tracking

Our publication *Scalable Multi-Domain Dialogue State Tracking (IEEE ASRU 2017)*
reports joint goal accuracy on Sim-R and Sim-M datasets. The released version of
the datasets includes fixes for some errors in dialogue state and action
annotations. This [updated version](https://arxiv.org/abs/1712.10224) of the
paper reports the results on corrected datasets.
