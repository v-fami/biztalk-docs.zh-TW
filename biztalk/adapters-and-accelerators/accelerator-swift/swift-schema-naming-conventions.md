---
title: SWIFT 結構描述命名慣例 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- naming conventions [schemas]
- schemas, naming conventions
ms.assetid: 3c1f2519-2575-4178-89c1-e97333c1e6bd
caps.latest.revision: 5
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: dabd9796497bdd5b81d34f71c01124f26de203d9
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "36987423"
---
# <a name="swift-schema-naming-conventions"></a><span data-ttu-id="bdd83-102">SWIFT 結構描述命名慣例</span><span class="sxs-lookup"><span data-stu-id="bdd83-102">SWIFT Schema Naming Conventions</span></span>
<span data-ttu-id="bdd83-103">Microsoft [!INCLUDE[A4SWIFT_CurrentVersion_FirstRef](../../includes/a4swift-currentversion-firstref-md.md)] Society 結構描述包含使用 BizTalk 編輯器所建立的全球 Interbank 財務電信 (SWIFT) FIN 訊息。</span><span class="sxs-lookup"><span data-stu-id="bdd83-103">Microsoft [!INCLUDE[A4SWIFT_CurrentVersion_FirstRef](../../includes/a4swift-currentversion-firstref-md.md)] includes schemas for Society for Worldwide Interbank Financial Telecommunication (SWIFT) FIN messages that were created using BizTalk Editor.</span></span> <span data-ttu-id="bdd83-104">這些結構描述符合整個下列慣例：</span><span class="sxs-lookup"><span data-stu-id="bdd83-104">These schemas conform to the following conventions throughout:</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="bdd83-105">所有結構描述的版本。</span><span class="sxs-lookup"><span data-stu-id="bdd83-105">All schemas are versioned.</span></span> <span data-ttu-id="bdd83-106">若要查看的版本，開啟[!INCLUDE[btsVStudioNoVersion](../../includes/btsvstudionoversion-md.md)]，以滑鼠右鍵按一下方案總管 中的結構描述。</span><span class="sxs-lookup"><span data-stu-id="bdd83-106">To see the version, open [!INCLUDE[btsVStudioNoVersion](../../includes/btsvstudionoversion-md.md)], and right-click the schema in Solution Explorer.</span></span> <span data-ttu-id="bdd83-107">具有\<結構描述\>選取在 「 BizTalk 編輯器 」 中，在 [屬性] 窗格向下捲動到 [標準版本] 屬性中的節點。</span><span class="sxs-lookup"><span data-stu-id="bdd83-107">With the \<Schema\> node selected in BizTalk Editor, in the Properties pane scroll down to the Standard Version property.</span></span>  
  
- <span data-ttu-id="bdd83-108">每個交換的結構描述檔案的名稱是**MT*xxx*.xsd**，其中*xxx* FIN 訊息類型。</span><span class="sxs-lookup"><span data-stu-id="bdd83-108">The name of each interchange schema file is **MT*xxx*.xsd**, where *xxx* is the FIN message type.</span></span>  
  
- <span data-ttu-id="bdd83-109">每個訊息的相關聯的主要原則檔案的名稱是**MT*xxx*_Master_Policy.xml**，而對應的名稱在商務規則引擎 (BRE) 是**MT*xxx*_Master_Policy**，清單名稱取代**MT*xxx*_PolicyList**。</span><span class="sxs-lookup"><span data-stu-id="bdd83-109">The name of the associated master policy file for each message is **MT*xxx*_Master_Policy.xml**, and the corresponding name in the Business Rule Engine (BRE) is **MT*xxx*_Master_Policy**, with a list name of **MT*xxx*_PolicyList**.</span></span>  
  
- <span data-ttu-id="bdd83-110">每個訊息的相關聯的驗證原則檔的名稱是**MT*xxx*_Validation_Policy.xml**，BRE 中對應的名稱，而且**MT*xxx*_Validation_Policy**。</span><span class="sxs-lookup"><span data-stu-id="bdd83-110">The name of the associated validation policy file for each message is **MT*xxx*_Validation_Policy.xml**, and the corresponding name in the BRE is **MT*xxx*_Validation_Policy**.</span></span>  
  
- <span data-ttu-id="bdd83-111">每個訊息結構描述中的根名稱是**SWIFT_CATEGORY*z*_MT*zxx*_Interchange**，其中*z*是訊息類別 （訊息類型的第一個數字） 和*zxx*是訊息類型。</span><span class="sxs-lookup"><span data-stu-id="bdd83-111">Within each message schema, the name of the root is **SWIFT_CATEGORY*z*_MT*zxx*_Interchange**, where *z* is the message category (first digit of the message type) and *zxx* is the message type.</span></span>  
  
- <span data-ttu-id="bdd83-112">每個訊息結構描述的目標命名空間是**<http://schemas.microsoft.com/BizTalk/Solutions/FinancialServices/SWIFT/Category*z*/MT*zxx>** <em>，其中 * z</em>是訊息分類 （訊息類型的第一個數字） 及*zxx*是訊息類型。</span><span class="sxs-lookup"><span data-stu-id="bdd83-112">The target namespace for each message schema is **<http://schemas.microsoft.com/BizTalk/Solutions/FinancialServices/SWIFT/Category*z*/MT*zxx>**<em>, where *z</em> is the message category (first digit of the message type) and *zxx* is the message type.</span></span>  
  
- <span data-ttu-id="bdd83-113">文件類型是**MT * zxx**<em>，其中 * zxx</em>是訊息類型。</span><span class="sxs-lookup"><span data-stu-id="bdd83-113">The document type is **MT*zxx**<em>, where *zxx</em> is the message type.</span></span>  
  
- <span data-ttu-id="bdd83-114">未編號的欄位和子欄位的名稱包含描述性的商務名稱。</span><span class="sxs-lookup"><span data-stu-id="bdd83-114">The names of fields that are not numbered and sub-fields include descriptive business names.</span></span> <span data-ttu-id="bdd83-115">每個單字的第一個字母大寫，而且名稱不包含多餘的空格或標點符號字與字之間 (例如，名稱會是**ServiceIdentifier**，而非**服務識別碼**).</span><span class="sxs-lookup"><span data-stu-id="bdd83-115">The first letter of each word is capitalized, and the names do not include an intervening space or punctuation between words (for example, the name would be **ServiceIdentifier**, not **Service Identifier**).</span></span>  
  
- <span data-ttu-id="bdd83-116">在訊息中的序列標籤符合*SWIFT 參考指南*(例如**SequenceA**)。</span><span class="sxs-lookup"><span data-stu-id="bdd83-116">The labels of sequences within messages conform to the *SWIFT Reference Guide* (for example, **SequenceA**).</span></span>  
  
- <span data-ttu-id="bdd83-117">標籤的編號 SWIFT 欄位包含描述性的標題，後面接著序列 （如果有的話），後面接著數字代碼和選擇性的字母格式 (例如**Reference_A_20C**)。</span><span class="sxs-lookup"><span data-stu-id="bdd83-117">The labels of numbered SWIFT fields include a descriptive title followed by the sequence (if present), followed by the number code and optional letter format (for example, **Reference_A_20C**).</span></span>  
  
- <span data-ttu-id="bdd83-118">當選擇多個欄位的格式時，節點的標籤是 **\<*選擇*\>**，和每個選項則是已編號的欄位 (例如**日期_A_98A**並**DateTime_A_98C**)。</span><span class="sxs-lookup"><span data-stu-id="bdd83-118">Where there is a choice of multiple formats for a field, the label of the node is **\<*Choice*\>**, and then each option is a numbered field (for example, **Date_A_98A** and **DateTime_A_98C**).</span></span>  
  
- <span data-ttu-id="bdd83-119">最低層級的項目定義的子欄位的名稱是由後面接著子欄位的名稱所組成**型別**(例如**accountType**帳戶)。</span><span class="sxs-lookup"><span data-stu-id="bdd83-119">The name of the lowest level element definition of a sub-field consists of the name of the sub-field followed by **Type** (for example, **accountType** for Account).</span></span>  
  
  <span data-ttu-id="bdd83-120">訊息結構描述中的其他命名空間包含下列各項：</span><span class="sxs-lookup"><span data-stu-id="bdd83-120">Other namespaces in the message schema include the following:</span></span>  
  
- <span data-ttu-id="bdd83-121">xmlns:xs="<http://www.w3.org/2001/XMLSchema>".</span><span class="sxs-lookup"><span data-stu-id="bdd83-121">xmlns:xs="<http://www.w3.org/2001/XMLSchema>".</span></span> <span data-ttu-id="bdd83-122">這是預設的 W3C XML 結構描述命名空間。</span><span class="sxs-lookup"><span data-stu-id="bdd83-122">This is the default W3C XML Schema namespace.</span></span>  
  
- <span data-ttu-id="bdd83-123">xmlns:b ="<http://schemas.microsoft.com/BizTalk/2003>」。</span><span class="sxs-lookup"><span data-stu-id="bdd83-123">xmlns:b="<http://schemas.microsoft.com/BizTalk/2003>".</span></span> <span data-ttu-id="bdd83-124">這是預設的 BizTalk 命名空間。</span><span class="sxs-lookup"><span data-stu-id="bdd83-124">This is the default BizTalk namespace.</span></span>  
  
  <span data-ttu-id="bdd83-125">每個訊息結構描述必須直接參考基底型別和通用結構描述資料型別。</span><span class="sxs-lookup"><span data-stu-id="bdd83-125">Each message schema directly references the base type and common data type schemas.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="bdd83-126">另請參閱</span><span class="sxs-lookup"><span data-stu-id="bdd83-126">See Also</span></span>  
 [<span data-ttu-id="bdd83-127">使用結構描述</span><span class="sxs-lookup"><span data-stu-id="bdd83-127">Working with Schemas</span></span>](../../adapters-and-accelerators/accelerator-swift/working-with-schemas.md)