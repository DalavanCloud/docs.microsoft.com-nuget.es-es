---
title: Gobierno de los proyectos de NuGet
description: Modelo de gobierno de NuGet, incluidos los roles y las responsabilidades de desarrolladores registrados, colaboradores y usuarios.
author: kraigb
ms.author: kraigb
manager: douge
ms.date: 01/18/2018
ms.topic: conceptual
ms.openlocfilehash: 37bfd146eefd52fd0332f3b99fa36651fc5c93d4
ms.sourcegitcommit: 3eab9c4dd41ea7ccd2c28bb5ab16f6fbbec13708
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 04/26/2018
---
# <a name="nuget-governance"></a><span data-ttu-id="3da8c-103">Gobierno de NuGet</span><span class="sxs-lookup"><span data-stu-id="3da8c-103">NuGet governance</span></span>

> <span data-ttu-id="3da8c-104">Este documento se basa en el modelo [Benevolent Dictator Governance Model](http://www.oss-watch.ac.uk/resources/benevolentdictatorgovernancemodel) de la Universidad de Oxford.</span><span class="sxs-lookup"><span data-stu-id="3da8c-104">This document is based upon the [Benevolent Dictator Governance Model](http://www.oss-watch.ac.uk/resources/benevolentdictatorgovernancemodel) by the University of Oxford.</span></span> <span data-ttu-id="3da8c-105">Tiene una licencia de tipo [Creative Commons Attribution-ShareAlike 2.0 UK: England & Wales License](http://creativecommons.org/licenses/by-sa/2.0/uk/).</span><span class="sxs-lookup"><span data-stu-id="3da8c-105">It is licensed under a [Creative Commons Attribution-ShareAlike 2.0 UK: England & Wales License](http://creativecommons.org/licenses/by-sa/2.0/uk/).</span></span>

<span data-ttu-id="3da8c-106">El proyecto de NuGet está dirigido por un dictador benevolente y está administrado por la comunidad.</span><span class="sxs-lookup"><span data-stu-id="3da8c-106">The NuGet project is led by a Benevolent Dictator and managed by the community.</span></span> <span data-ttu-id="3da8c-107">Es decir, la comunidad contribuye activamente en el mantenimiento diario del proyecto, pero la línea estratégica general la lleva el dictador benevolente.</span><span class="sxs-lookup"><span data-stu-id="3da8c-107">That is, the community actively contributes to the day-to-day maintenance of the project, but the general strategic line is drawn by the benevolent dictator.</span></span> <span data-ttu-id="3da8c-108">En caso de desacuerdo, el dictador benevolente tiene la última palabra.</span><span class="sxs-lookup"><span data-stu-id="3da8c-108">In case of disagreement, the benevolent dictator has the last word.</span></span>

<span data-ttu-id="3da8c-109">Es tarea del dictador benevolente resolver los conflictos producidos en la comunidad y asegurarse de que el proyecto puede avanzar de una manera coordinada.</span><span class="sxs-lookup"><span data-stu-id="3da8c-109">It is the benevolent dictator’s job to resolve disputes within the community and to ensure that the project is able to progress in a coordinated way.</span></span> <span data-ttu-id="3da8c-110">A su vez, es tarea de la comunidad guiar las decisiones del dictador benevolente mediante el compromiso y la colaboración activos.</span><span class="sxs-lookup"><span data-stu-id="3da8c-110">In turn, it's the community’s job to guide the decisions of the benevolent dictator through active engagement and contribution.</span></span>

## <a name="roles-and-responsibilities"></a><span data-ttu-id="3da8c-111">Roles y responsabilidades</span><span class="sxs-lookup"><span data-stu-id="3da8c-111">Roles and responsibilities</span></span>

<span data-ttu-id="3da8c-112">Aquí se describen cuatro roles: Dictador benevolente, Desarrolladores registrados, Colaboradores y Usuarios.</span><span class="sxs-lookup"><span data-stu-id="3da8c-112">There are four roles described here: Benevolent Dictator, Committers, Contributors, and Users.</span></span>

### <a name="benevolent-dictator"></a><span data-ttu-id="3da8c-113">Dictador benevolente</span><span class="sxs-lookup"><span data-stu-id="3da8c-113">Benevolent dictator</span></span>

<span data-ttu-id="3da8c-114">El equipo básico de NuGet se autoproclama dictador benevolente o jefe de proyecto,</span><span class="sxs-lookup"><span data-stu-id="3da8c-114">The NuGet core team is self-appointed as Benevolent Dictator or project lead.</span></span> <span data-ttu-id="3da8c-115">pero como la comunidad siempre tiene la capacidad de desviarse, el equipo es responsable directo de la comunidad.</span><span class="sxs-lookup"><span data-stu-id="3da8c-115">However, because the community always has the ability to fork, the team is fully answerable to the community.</span></span> <span data-ttu-id="3da8c-116">El jefe de proyecto debe entender la comunidad como un todo y esforzarse para satisfacer al máximo las necesidades relacionadas con los conflictos, así como asegurarse de que el proyecto sobreviva a largo plazo.</span><span class="sxs-lookup"><span data-stu-id="3da8c-116">The project lead is expected to understand the community as a whole and strive to satisfy as many conflicting needs as possible, while ensuring that the project survives in the long term.</span></span>

<span data-ttu-id="3da8c-117">En muchos sentidos, el rol del dictador benevolente tiene menos que ver con una dictadura y más con la diplomacia.</span><span class="sxs-lookup"><span data-stu-id="3da8c-117">In many ways, the role of the benevolent dictator is less about dictatorship and more about diplomacy.</span></span> <span data-ttu-id="3da8c-118">La clave consiste en asegurarse de que, a medida que el proyecto se amplíe, se proporcione influencia a las personas adecuadas sobre este y de que la comunidad apoye la visión del jefe de proyecto.</span><span class="sxs-lookup"><span data-stu-id="3da8c-118">The key is to ensure that, as the project expands, the right people are given influence over it and the community rallies behind the vision of the project lead.</span></span> <span data-ttu-id="3da8c-119">Por lo tanto, la tarea del jefe de proyecto es asegurarse de que los desarrolladores registrados (vea más abajo) toman las decisiones correctas en nombre del proyecto.</span><span class="sxs-lookup"><span data-stu-id="3da8c-119">The lead’s job is then to ensure that the committers (see below) make the right decisions on behalf of the project.</span></span> <span data-ttu-id="3da8c-120">Por lo general, siempre que los desarrolladores registrados se alineen con la estrategia del proyecto, el jefe de proyecto les permitirá proceder como quieran.</span><span class="sxs-lookup"><span data-stu-id="3da8c-120">Generally speaking, as long as the committers are aligned with the project’s strategy, the project lead will allow them to proceed as they desire.</span></span>

<span data-ttu-id="3da8c-121">Además, el personal de .NET Foundation considera que el jefe de proyecto es el primer punto de contacto o el punto de contacto principal para NuGet para fines de operaciones comerciales, incluidos los registros de dominio y los servicios técnicos (por ejemplo, la firma de código).</span><span class="sxs-lookup"><span data-stu-id="3da8c-121">Additionally, .NET Foundation staff consider the project lead the primary or first point of contact for NuGet for purposes of business operations including domain registrations, and technical services (e.g. code-signing).</span></span>

### <a name="committers"></a><span data-ttu-id="3da8c-122">Desarrolladores registrados</span><span class="sxs-lookup"><span data-stu-id="3da8c-122">Committers</span></span>

<span data-ttu-id="3da8c-123">Los autores son colaboradores que han llevado a cabo contribuciones valiosas prolongadas en NuGet y son designados por el dictador benevolente.</span><span class="sxs-lookup"><span data-stu-id="3da8c-123">Committers are contributors who have made sustained valuable contributions to NuGet and are appointed by the Benevolent Dictator.</span></span> <span data-ttu-id="3da8c-124">Una vez designados, se espera que los desarrolladores registrados escriban código directamente en el repositorio y protejan las contribuciones de los demás.</span><span class="sxs-lookup"><span data-stu-id="3da8c-124">Once appointed, committers are relied upon to both write code directly to the repository and screen the contributions of others.</span></span> <span data-ttu-id="3da8c-125">Aunque los desarrolladores registrados son desarrolladores, pueden contribuir de otros modos.</span><span class="sxs-lookup"><span data-stu-id="3da8c-125">Committers are often developers but can contribute in other ways.</span></span>

<span data-ttu-id="3da8c-126">Normalmente, un desarrollador registrado se centra en un aspecto específico del proyecto y aporta un nivel de conocimiento y comprensión que le merece el respeto de la comunidad y del jefe de proyecto.</span><span class="sxs-lookup"><span data-stu-id="3da8c-126">Typically, a committer focuses on a specific aspect of the project, and brings a level of expertise and understanding that earns them the respect of the community and the project lead.</span></span> <span data-ttu-id="3da8c-127">El rol del desarrollador registrado no es oficial. Se trata de una mera posición que asumen los miembros destacados de la comunidad, ya que el jefe de proyecto recurre a él en busca de ayuda y apoyo.</span><span class="sxs-lookup"><span data-stu-id="3da8c-127">The role of committer is not an official one, it's simply a position that influential members of the community assume as the project lead looks to them for guidance and support.</span></span>

<span data-ttu-id="3da8c-128">Los desarrolladores registrados no cuentan con autoridad en lo que a la dirección general de NuGet se refiere,</span><span class="sxs-lookup"><span data-stu-id="3da8c-128">Committers have no authority where the overall direction of NuGet is concerned.</span></span> <span data-ttu-id="3da8c-129">pero influyen al jefe de proyecto.</span><span class="sxs-lookup"><span data-stu-id="3da8c-129">However, they do have the ear of the project lead.</span></span> <span data-ttu-id="3da8c-130">Es tarea de un desarrollador registrado asegurarse de que el jefe de proyecto sea consciente de las necesidades y los objetivos colectivos de la comunidad, así como ayudar a desarrollar o desencadenar contribuciones adecuadas para el proyecto.</span><span class="sxs-lookup"><span data-stu-id="3da8c-130">It is a committer’s job to ensure that the lead is aware of the community’s needs and collective objectives, and to help develop or elicit appropriate contributions to the project.</span></span> <span data-ttu-id="3da8c-131">A veces, a los autores se les ofrece control informal sobre sus áreas de responsabilidad específicas y se les asignan derechos para modificar directamente ciertas áreas del código fuente.</span><span class="sxs-lookup"><span data-stu-id="3da8c-131">Often, committers are given informal control over their specific areas of responsibility, and are assigned rights to directly modify certain areas of the source code.</span></span> <span data-ttu-id="3da8c-132">Es decir, aunque los desarrolladores registrados no cuentan con autoridad explícita para tomar decisiones, muchas veces verán que sus acciones equivalen a las decisiones que ha tomado el jefe de proyecto.</span><span class="sxs-lookup"><span data-stu-id="3da8c-132">That is, although committers do not have explicit decision-making authority, they will often find that their actions are synonymous with the decisions made by the lead.</span></span>

### <a name="contributors"></a><span data-ttu-id="3da8c-133">Colaboradores</span><span class="sxs-lookup"><span data-stu-id="3da8c-133">Contributors</span></span>

<span data-ttu-id="3da8c-134">Los colaboradores son miembros de la comunidad que envían revisiones a NuGet.</span><span class="sxs-lookup"><span data-stu-id="3da8c-134">Contributors are community members who submit patches to NuGet.</span></span> <span data-ttu-id="3da8c-135">Estas revisiones pueden ser únicas o se producen con el tiempo.</span><span class="sxs-lookup"><span data-stu-id="3da8c-135">These patches may be a one-time occurrence or occur over time.</span></span> <span data-ttu-id="3da8c-136">Se prevé que los colaboradores envíen revisiones que sean pequeñas al principio y que aumenten de tamaño cuando el colaborador, los desarrolladores registrados y el jefe de proyecto hayan ganado confianza en la calidad de las revisiones de un colaborador.</span><span class="sxs-lookup"><span data-stu-id="3da8c-136">Expectations are that contributors submit patches that are small at first and grow larger when the contributor, committers, and the project lead have built confidence in the quality of a contributor's patches.</span></span> <span data-ttu-id="3da8c-137">Los colaboradores se reconocen en el documento de notas de la versión del producto asociado.</span><span class="sxs-lookup"><span data-stu-id="3da8c-137">Contributors are recognized in the associated product release notes document.</span></span>

<span data-ttu-id="3da8c-138">Antes de que se inserte en el repositorio la primera revisión de un colaborador, debe firmar un [contrato de licencia para colaboradores](http://en.wikipedia.org/wiki/Contributor_License_Agreement) o un contrato de asignación con .NET Foundation.</span><span class="sxs-lookup"><span data-stu-id="3da8c-138">Before a contributor’s first patch is put into the repository, they must sign a [Contributor License Agreement](http://en.wikipedia.org/wiki/Contributor_License_Agreement) or an assignment agreement to the .NET Foundation.</span></span> <span data-ttu-id="3da8c-139">La revisión se puede enviar y debatir, pero no se puede destinar al repositorio si no se dispone de los documentos adecuados en vigor.</span><span class="sxs-lookup"><span data-stu-id="3da8c-139">The patch can be submitted and discussed but it can’t actually be committed to the repository without the appropriate paperwork in place.</span></span> <span data-ttu-id="3da8c-140">Para obtener un contrato de licencia de colaborador, envíe una solicitud por correo electrónico a [contributions@nuget.org](mailto:contributions@nuget.org).</span><span class="sxs-lookup"><span data-stu-id="3da8c-140">To obtain a contributor license agreement, please send a request in email to [contributions@nuget.org](mailto:contributions@nuget.org).</span></span>

<span data-ttu-id="3da8c-141">Para convertirse en un colaborador, envíe una solicitud de incorporación de cambios a uno de los siguientes repositorios:</span><span class="sxs-lookup"><span data-stu-id="3da8c-141">To become a contributor, submit a pull request to one of the following repositories:</span></span>

- [<span data-ttu-id="3da8c-142">Cliente de NuGet</span><span class="sxs-lookup"><span data-stu-id="3da8c-142">NuGet Client</span></span>](https://github.com/NuGet/NuGet.Client)
- [<span data-ttu-id="3da8c-143">Galería de NuGet</span><span class="sxs-lookup"><span data-stu-id="3da8c-143">NuGet Gallery</span></span>](https://github.com/nuget/nugetgallery)
- [<span data-ttu-id="3da8c-144">Documentos de NuGet</span><span class="sxs-lookup"><span data-stu-id="3da8c-144">NuGet Docs</span></span>](https://github.com/nuget/nugetdocs)

<span data-ttu-id="3da8c-145">El proceso detallado para enviar una solicitud de incorporación de cambios varía según el repositorio:</span><span class="sxs-lookup"><span data-stu-id="3da8c-145">The detailed process for submitting a pull request varies by repository:</span></span>

- [<span data-ttu-id="3da8c-146">Instrucciones de colaboración para el cliente de NuGet y la galería de NuGet</span><span class="sxs-lookup"><span data-stu-id="3da8c-146">Contribution instructions for NuGet Client and NuGet Gallery</span></span>](https://github.com/NuGet/Home/wiki/Contributing-to-NuGet)
- [<span data-ttu-id="3da8c-147">Instrucciones de colaboración para los documentos de NuGet</span><span class="sxs-lookup"><span data-stu-id="3da8c-147">Contribution instructions for NuGet Docs</span></span>](https://github.com/NuGet/NuGetDocs/wiki/Contributing-to-NuGet-Documentation)

### <a name="users"></a><span data-ttu-id="3da8c-148">Usuarios</span><span class="sxs-lookup"><span data-stu-id="3da8c-148">Users</span></span>

<span data-ttu-id="3da8c-149">Los usuarios son miembros de la comunidad que necesitan y usan NuGet, como los consumidores o los autores de paquetes.</span><span class="sxs-lookup"><span data-stu-id="3da8c-149">Users are community members who have a need for and use NuGet, as package consumers and/or authors.</span></span> <span data-ttu-id="3da8c-150">Los usuarios son los miembros más importantes de la comunidad: sin ellos, el proyecto no tendría ningún propósito.</span><span class="sxs-lookup"><span data-stu-id="3da8c-150">Users are the most important members of the community: without them, the project would have no purpose.</span></span> <span data-ttu-id="3da8c-151">Cualquier persona puede ser un usuario; no hay ningún requisito específico.</span><span class="sxs-lookup"><span data-stu-id="3da8c-151">Anyone can be a user; there are no specific requirements.</span></span>

<span data-ttu-id="3da8c-152">Se debe alentar a los usuarios para que participen en la vida de NuGet y en la comunidad tanto como sea posible.</span><span class="sxs-lookup"><span data-stu-id="3da8c-152">Users should be encouraged to participate in the life of NuGet and the community as much as possible.</span></span> <span data-ttu-id="3da8c-153">Las contribuciones de los usuarios permiten que el equipo del proyecto se asegure de que satisface las necesidades de esos usuarios.</span><span class="sxs-lookup"><span data-stu-id="3da8c-153">User contributions enable the project team to ensure that they are satisfying the needs of those users.</span></span> <span data-ttu-id="3da8c-154">Algunas de las actividades de usuario habituales son las siguientes:</span><span class="sxs-lookup"><span data-stu-id="3da8c-154">Common user activities include but are not limited to the following:</span></span>

- <span data-ttu-id="3da8c-155">Recomendar el uso del proyecto</span><span class="sxs-lookup"><span data-stu-id="3da8c-155">Advocating for use of the project</span></span>
- <span data-ttu-id="3da8c-156">Informar a los desarrolladores de las ventajas y desventajas del proyecto desde la perspectiva de un usuario nuevo</span><span class="sxs-lookup"><span data-stu-id="3da8c-156">Informing developers of project strengths and weaknesses from a new user’s perspective</span></span>
- <span data-ttu-id="3da8c-157">Proporcionar apoyo moral (un "Gracias" ayuda)</span><span class="sxs-lookup"><span data-stu-id="3da8c-157">Providing moral support (a thank you goes a long way)</span></span>
- <span data-ttu-id="3da8c-158">Escribir documentación y tutoriales</span><span class="sxs-lookup"><span data-stu-id="3da8c-158">Writing documentation and tutorials</span></span>
- <span data-ttu-id="3da8c-159">Cumplimentar informes de errores y solicitudes de características</span><span class="sxs-lookup"><span data-stu-id="3da8c-159">Filing bug reports and feature requests</span></span>
- <span data-ttu-id="3da8c-160">Participar en eventos de la comunidad, como búsqueda de errores</span><span class="sxs-lookup"><span data-stu-id="3da8c-160">Participating in community events, such as bug bashes</span></span>
- <span data-ttu-id="3da8c-161">Participa en paneles de discusión o foros</span><span class="sxs-lookup"><span data-stu-id="3da8c-161">Participating on discussion boards or forums</span></span>

<span data-ttu-id="3da8c-162">Los usuarios que sigan interactuando con el proyecto y su comunidad verán que se irán implicando más y más.</span><span class="sxs-lookup"><span data-stu-id="3da8c-162">Users who continue to engage with the project and its community will often find themselves becoming more and more involved.</span></span> <span data-ttu-id="3da8c-163">Luego, estos usuarios pueden continuar para convertirse en colaboradores, tal y como se describe arriba.</span><span class="sxs-lookup"><span data-stu-id="3da8c-163">Such users may then go on to become contributors, as described above.</span></span>

## <a name="package-succession-under-special-circumstances"></a><span data-ttu-id="3da8c-164">Sucesión de paquetes en circunstancias especiales</span><span class="sxs-lookup"><span data-stu-id="3da8c-164">Package succession under special circumstances</span></span>

<span data-ttu-id="3da8c-165">En el desafortunado caso de que el titular de una cuenta de NuGet quede incapacitado o fallezca, trabajaremos con la comunidad para agregar los propietarios adecuados al paquete en el que dicha cuenta tiene una propiedad única y el paquete se publique con una [licencia aprobada por OSI](https://opensource.org/licenses/alphabetical).</span><span class="sxs-lookup"><span data-stu-id="3da8c-165">In the unfortunate situation where a NuGet account holder is incapacitated or deceased, we’ll work with the community to add appropriate owner/s to the package where the said account has sole ownership and the package is published under an [OSI approved license](https://opensource.org/licenses/alphabetical).</span></span> <span data-ttu-id="3da8c-166">Para solicitar la propiedad, debe enviar los siguientes documentos:</span><span class="sxs-lookup"><span data-stu-id="3da8c-166">To request ownership you must send us the following documents:</span></span>

1. <span data-ttu-id="3da8c-167">Una fotocopia de su documento identificativo con foto, emitido por su gobierno.</span><span class="sxs-lookup"><span data-stu-id="3da8c-167">A photocopy of your government-issued photo ID.</span></span>
1. <span data-ttu-id="3da8c-168">Uno de los siguientes documentos, en los que se demuestre el estado anterior del titular de la cuenta:</span><span class="sxs-lookup"><span data-stu-id="3da8c-168">One of the following documents proving the previous account holder’s status:</span></span> 
    - <span data-ttu-id="3da8c-169">Un certificado de defunción oficial, emitido por su gobierno, en el caso de que el anterior titular de la cuenta haya fallecido; o bien</span><span class="sxs-lookup"><span data-stu-id="3da8c-169">An official, government-issued death certificate if the previous account holder is deceased, or,</span></span>
    - <span data-ttu-id="3da8c-170">Un documento certificado, como un certificado firmado por un profesional de la salud a cargo de la salud de un titular de una cuenta incapacitado.</span><span class="sxs-lookup"><span data-stu-id="3da8c-170">A certified document such as a certificate signed by a medical professional in charge of the care of an incapacitated account holder.</span></span>
1. <span data-ttu-id="3da8c-171">Uno de los siguientes documentos, en los que se demuestre su derecho a la propiedad:</span><span class="sxs-lookup"><span data-stu-id="3da8c-171">One of the following documents proving your right to ownership:</span></span> 
    - <span data-ttu-id="3da8c-172">Certificado de matrimonio en el que se muestre que es el cónyuge superviviente del titular de la cuenta,</span><span class="sxs-lookup"><span data-stu-id="3da8c-172">Marriage certificate showing that you are the surviving spouse of the account holder,</span></span>
    - <span data-ttu-id="3da8c-173">Poderes firmados,</span><span class="sxs-lookup"><span data-stu-id="3da8c-173">Signed power of attorney,</span></span>
    - <span data-ttu-id="3da8c-174">Copia de un testamento o de un documento de fideicomiso en el que se le nombre albacea o legatario,</span><span class="sxs-lookup"><span data-stu-id="3da8c-174">Copy of a will or trust document naming you as executor or beneficiary,</span></span>
    - <span data-ttu-id="3da8c-175">Certificado de nacimiento del titular de la cuenta, si es su progenitor, o bien</span><span class="sxs-lookup"><span data-stu-id="3da8c-175">Birth certificate for the account holder, if you are their parent, or,</span></span>
    - <span data-ttu-id="3da8c-176">Documentación de tutela si es tutor legal del titular de la cuenta.</span><span class="sxs-lookup"><span data-stu-id="3da8c-176">Guardianship paperwork if you are a legal guardian of the account holder.</span></span>

<span data-ttu-id="3da8c-177">Si necesita invocar esta directiva, envíenos un correo electrónico a [support@nuget.org](mailto:support@nuget.org) con el identificador y la versión del paquete.</span><span class="sxs-lookup"><span data-stu-id="3da8c-177">If you find yourself in need of invoking this policy, please send us an email at [support@nuget.org](mailto:support@nuget.org) with the ID and version of the package.</span></span>

## <a name="transparency"></a><span data-ttu-id="3da8c-178">Transparencia</span><span class="sxs-lookup"><span data-stu-id="3da8c-178">Transparency</span></span>

<span data-ttu-id="3da8c-179">Que la comunidad confíe en el gobierno de un proyecto de código abierto es esencial para que este tenga éxito.</span><span class="sxs-lookup"><span data-stu-id="3da8c-179">Building community trust in the governance of an open-source project is vital to its success.</span></span> <span data-ttu-id="3da8c-180">Para ello, se debe tomar una decisión de forma transparente y clara.</span><span class="sxs-lookup"><span data-stu-id="3da8c-180">To that end, decision making must be done in a transparent, open fashion.</span></span> <span data-ttu-id="3da8c-181">El debate sobre la dirección del proyecto debe tener lugar de forma pública.</span><span class="sxs-lookup"><span data-stu-id="3da8c-181">Discussion about the project’s direction must be done publicly.</span></span> <span data-ttu-id="3da8c-182">La comunidad no debe verse sorprendida nunca por una decisión que haya tomado el dictador benevolente.</span><span class="sxs-lookup"><span data-stu-id="3da8c-182">The community should never be caught off-guard by a decision by the Benevolent Dictator.</span></span> <span data-ttu-id="3da8c-183">Además, el debate sobre las decisiones del proyecto se debe archivar para que los miembros de la comunidad puedan comprender toda la historia de una decisión y su contexto.</span><span class="sxs-lookup"><span data-stu-id="3da8c-183">Additionally, discussion about project decisions must be archived so that community members can understand the entire history of a decision and its context.</span></span>