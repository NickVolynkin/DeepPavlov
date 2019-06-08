Conceptual overview
===================

Our goal is to enable AI-application developers and researchers with:

-  set of pre-trained NLP models, pre-defined dialog system components
   (ML/DL/Rule-based) and pipeline templates;
-  a framework for implementing and testing their own dialog models;
-  tools for application integration with adjacent infrastructure
   (messengers, helpdesk software etc.);
-  benchmarking environment for conversational models and uniform access
   to relevant datasets.

.. image:: ../_static/dp_agnt_diag.png


Key Concepts
------------

.. glossary::

    Agent
    Conversational agent
        a program, communicating with users in natural language (text).

    Skill
        agent's ability to fulfill user’s goal in a particular domain. Typically, this is
        accomplished by presenting information or completing transaction
        (e.g. answering question by FAQ, booking tickets etc.). However, for
        some tasks success of interaction is defined as continuous
        engagement (e.g. chit-chat).

        Represented by :py:class:`Skill <deeppavlov.core.skill.skill.Skill>` class.


    Component
        a reusable functional part of :term:`skill`.

        Represented by :py:class:`Component <deeppavlov.core.models.component.Component>` class.

    Model
        (needs definition)

    Training
        (needs definition)

    Rule-based model
        model, based on strict logic (rules).
        Rule-based models cannot be trained.

    Machine learning model
    ML model
        model, based on ___.
        Can only be trained independently.

    Deep learning model
    DL model
    Neural network
        model, based on ___.
        Deep learning models can be trained independently or in an
        end-to-end mode being joined in a chain.

    Skill manager

         Agent's part that selects the :term:`skill` to generate response.

    Chainer

        Agent's part that builds an :term:`agent`/:term:`component` pipeline from heterogeneous
        components (Rule-based/ML/DL). It allows to train and infer models in
        a pipeline as a whole.

        Represented by :py:class:`Chainer <deeppavlov.core.common.chainer.Chainer>` class.

The smallest building block of the library is ``Component``.
``Component`` stands for any kind of function in an NLP pipeline. It can
be implemented as a neural network, a non-neural ML model or a
rule-based system. Besides that, ``Component`` can have nested
structure, i.e. a ``Component`` can include other ``Component`` s.

``Component`` s can be joined into a ``Skill``. ``Skill`` solves a
larger NLP task compared to ``Component``. However, in terms of
implementation ``Skill``\ s are not different from ``Component``\ s. The
only restriction of ``Skill``\ s is that their input and output should
both be strings. Therefore, ``Skill``\ s are usually associated with
dialogue tasks.

``Agent`` is supposed to be a multi-purpose dialogue system that
comprises several ``Skill``\ s and can switch between them. It can be a
dialogue system that contains a goal-oriented and chatbot skills and
chooses which one to use for generating the answer depending on user
input.

DeepPavlov is built on top of machine learning frameworks
`TensorFlow <https://www.tensorflow.org/>`__ and
`Keras <https://keras.io/>`__. Other external libraries can be used to
build basic components.
