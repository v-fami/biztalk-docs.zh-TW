---
title: 建立和部署原則的新訊息類型 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 43343238-ec45-44ed-a230-9e234bd22d05
caps.latest.revision: ''
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: b826b3ee9408caf91fe5adcb2177d709f885a6e1
ms.sourcegitcommit: 8418b1a8f38b7f56979cd6e203f0b591e2f40fe1
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/28/2018
---
# <a name="creating-and-deploying-policies-for-new-message-types"></a><span data-ttu-id="59247-102">建立和部署原則的新訊息類型</span><span class="sxs-lookup"><span data-stu-id="59247-102">Creating and Deploying Policies for New Message Types</span></span>
<span data-ttu-id="59247-103">若要建立並部署新的訊息類型的原則：</span><span class="sxs-lookup"><span data-stu-id="59247-103">To create and deploy policies for new message types:</span></span>  
  
1.  <span data-ttu-id="59247-104">建立 MX 訊息資料夾內的訊息類型名稱的資料夾。</span><span class="sxs-lookup"><span data-stu-id="59247-104">Create a folder with the name of the message type inside MX Messages folder.</span></span> <span data-ttu-id="59247-105">例如，在此情況下名稱會是資料夾的 setr.004.001.02。</span><span class="sxs-lookup"><span data-stu-id="59247-105">For example, in this case the name of the folder would be setr.004.001.02.</span></span>  
  
    ```csharp  
    (<xs:complexType name="Document">  
        <xs:sequence>  
            <xs:element name="setr.004.001.02" type="setr.004.001.02"/>  
        </xs:sequence>  
    </xs:complexType>)  
    ```  
  
2.  <span data-ttu-id="59247-106">將結構描述檔案 (\*.xsd)，以及產生的主要 / 驗證原則檔，以取得此訊息類型，此資料夾中。</span><span class="sxs-lookup"><span data-stu-id="59247-106">Place the schema file (\*.xsd) along with the resulting master / validation policy file for this message type in this folder.</span></span>  
  
3.  <span data-ttu-id="59247-107">更新關鍵字名稱 MXMessageTypeKeywordList.xml (C:\Program Files\Microsoft BizTalk Accelerator for SWIFT\SDK\Tools)。</span><span class="sxs-lookup"><span data-stu-id="59247-107">Update the MXMessageTypeKeywordList.xml (C:\Program Files\Microsoft BizTalk Accelerator for SWIFT\SDK\Tools) with a keyword name.</span></span> <span data-ttu-id="59247-108">此名稱必須是訊息的資料夾名稱的前四個字母。</span><span class="sxs-lookup"><span data-stu-id="59247-108">This name must be the first four letters of the message folder name.</span></span> <span data-ttu-id="59247-109">例如，</span><span class="sxs-lookup"><span data-stu-id="59247-109">For example,</span></span>  
  
    ```csharp  
    (<Keyword name ="setr" />)  
    ```  
  
4.  <span data-ttu-id="59247-110">若要建立特定的主要 / 驗證原則，製作的主要複本] / [現有的驗證原則檔訊息，並將它放在新的郵件資料夾。</span><span class="sxs-lookup"><span data-stu-id="59247-110">To create specific master / validation policies, take a copy of the master / validation policy files of the existing message and place it in the new message folder.</span></span>  
  
5.  <span data-ttu-id="59247-111">在 master 中的訊息類型參考的所有變更 / 驗證原則，以反映新的訊息類型。</span><span class="sxs-lookup"><span data-stu-id="59247-111">Change all of the references to message types in the master / validation policy to reflect the new message types.</span></span>  
  
## <a name="message-naming-conventions"></a><span data-ttu-id="59247-112">訊息的命名慣例</span><span class="sxs-lookup"><span data-stu-id="59247-112">Message Naming Conventions</span></span>  
 <span data-ttu-id="59247-113">請依照下列訊息名稱的這些的慣例：</span><span class="sxs-lookup"><span data-stu-id="59247-113">Follow these conventions for message names:</span></span>  
  
-   <span data-ttu-id="59247-114">**將訊息名稱取代**： 如果新的訊息名稱是 swift.if.ia.setr.004.001.02，舊的原則檔都已使用的訊息是 pacs.002.001.02 然後取代所有與 pacs.002.001.02 的項目swift.if.ia.setr.004.001.02 原則檔案中。</span><span class="sxs-lookup"><span data-stu-id="59247-114">**Replacing the message name**: If the new message name is swift.if.ia.setr.004.001.02 and the old message whose policy files have been used is pacs.002.001.02, then replace all of the occurrences of pacs.002.001.02 with swift.if.ia.setr.004.001.02 within the policy files.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="59247-115">訊息名稱是已下載的結構描述檔案的名稱，而且訊息類型的訊息中的文件類型名稱。</span><span class="sxs-lookup"><span data-stu-id="59247-115">Message name is the name of the schema file which has been downloaded and message type is the name of the document type in the message.</span></span>  
  
-   <span data-ttu-id="59247-116">保留原則檔案的名稱與相同的訊息結構描述本身。</span><span class="sxs-lookup"><span data-stu-id="59247-116">Keep the name of the policy files the same as the message schema itself.</span></span> <span data-ttu-id="59247-117">例如，swift.if.ia.setr.004.001.02.xsd 會有下列原則 swift.if.ia.setr.004.001.02 _Master_Policy.xml 和 swift.if.ia.setr.004.001.02 _Validation_Policy.xml。</span><span class="sxs-lookup"><span data-stu-id="59247-117">For example, swift.if.ia.setr.004.001.02.xsd will have following policies swift.if.ia.setr.004.001.02 _Master_Policy.xml and swift.if.ia.setr.004.001.02 _Validation_Policy.xml.</span></span>  
  
-   <span data-ttu-id="59247-118">**特殊字元**： 如果訊息名稱中，有任何特殊字元，則建立的原則檔，需要稍微不同的慣例。</span><span class="sxs-lookup"><span data-stu-id="59247-118">**Special characters**: If the message name has any special characters in it, then creating a policy file requires a slightly different convention.</span></span> <span data-ttu-id="59247-119">如果訊息名稱，比方說，swift.if.ia$setr.004.001.02，則您必須以訊息名稱變更原則檔案的名稱，含有要取代特殊字元"。"</span><span class="sxs-lookup"><span data-stu-id="59247-119">If the message name is, for example, swift.if.ia$setr.004.001.02, then you must change the name of the policy file to the message name with the special characters being replaced by “.”</span></span> <span data-ttu-id="59247-120">例如，如果 swift.if.ia$setr.004.001.02.xsd 訊息結構描述檔案的名稱，則產生的主要原則是 swift.if.ia.setr.004.001.02_Master_Policy.xml。</span><span class="sxs-lookup"><span data-stu-id="59247-120">For example, if the name of the message schema file is swift.if.ia$setr.004.001.02.xsd, then the resulting master policy would be swift.if.ia.setr.004.001.02_Master_Policy.xml.</span></span>  
  
     <span data-ttu-id="59247-121">主要的原則檔也需要變更以反映新的名稱，在下列標記：</span><span class="sxs-lookup"><span data-stu-id="59247-121">The master policy file also needs to be changed to reflect the new name in the following tags:</span></span>  
  
    -   <span data-ttu-id="59247-122">\<ruleset name="swift.if.ia.setr.004.001.02_Master_Policy"\></span><span class="sxs-lookup"><span data-stu-id="59247-122">\<ruleset name="swift.if.ia.setr.004.001.02_Master_Policy"\></span></span>  
  
    -   <span data-ttu-id="59247-123"><rule name="swift.if.ia.setr.004.001.02_Policy_List"</span><span class="sxs-lookup"><span data-stu-id="59247-123"><rule name="swift.if.ia.setr.004.001.02_Policy_List"</span></span>