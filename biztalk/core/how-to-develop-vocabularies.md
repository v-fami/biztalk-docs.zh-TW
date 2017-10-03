---
title: "如何開發詞彙 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- creating, vocabularies
- vocabularies, business rules
- business rules, vocabularies
- vocabularies, creating
ms.assetid: 5c16eb98-2257-44f2-8a29-899e02f7e556
caps.latest.revision: "8"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 2644cc938cbe5e42f4e124453d863741755d965d
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="how-to-develop-vocabularies"></a><span data-ttu-id="34a68-102">如何開發詞彙</span><span class="sxs-lookup"><span data-stu-id="34a68-102">How to Develop Vocabularies</span></span>
<span data-ttu-id="34a68-103">規則條件和動作是以可能有冗長且難於閱讀的繫結資訊之來源為基礎，這些資訊幾乎或根本無法告訴使用者它們指的是什麼。</span><span class="sxs-lookup"><span data-stu-id="34a68-103">Rule conditions and actions are based on sources that may have detailed, difficult-to-read binding information that tells the user little or nothing about what they refer to.</span></span> <span data-ttu-id="34a68-104">「商業規則架構」可讓您建立詞彙以簡化規則的開發，即透過提供使用者直覺和網域特定的詞彙，讓使用者可以聯想到規則條件和動作。</span><span class="sxs-lookup"><span data-stu-id="34a68-104">The Business Rules Framework enables you to create vocabularies to simplify the development of rules by offering users intuitive, domain-specific terminology that users can associate with rule conditions and actions.</span></span>  
  
 <span data-ttu-id="34a68-105">您可以指出要使用的資料來源、建立新詞彙，以及新增詞彙定義。</span><span class="sxs-lookup"><span data-stu-id="34a68-105">You can identify data sources to use, create a new vocabulary, and add vocabulary definitions to it.</span></span> <span data-ttu-id="34a68-106">您可以將自己的詞彙版本儲存至規則存放區，而且當它已完整時，您可以將它發佈以提供使用者定義正確且不變並繫結至資料參考的詞彙集。</span><span class="sxs-lookup"><span data-stu-id="34a68-106">You can save a version of your vocabulary to the rule store, and when it is complete, you can publish it to provide users with a well-defined, immutable set of terms that are bound to data references.</span></span>  
  
 <span data-ttu-id="34a68-107">若將來需要變更詞彙，可以直接建立新版本的詞彙以反映變更。</span><span class="sxs-lookup"><span data-stu-id="34a68-107">If you need to make changes to your vocabulary in the future, you can simply create a new version of the vocabulary that reflects the changes.</span></span>  
  
> [!CAUTION]
>  <span data-ttu-id="34a68-108">當新版本的詞彙已建立時，從舊版本建立的規則仍然會指向舊版本。</span><span class="sxs-lookup"><span data-stu-id="34a68-108">When a new version of a vocabulary is created, the rules built from a previous version will still point to the previous version.</span></span>  
  
### <a name="to-create-a-vocabulary"></a><span data-ttu-id="34a68-109">建立詞彙</span><span class="sxs-lookup"><span data-stu-id="34a68-109">To create a vocabulary</span></span>  
  
1.  <span data-ttu-id="34a68-110">在 事實總管 視窗中，按一下**詞彙** 索引標籤。</span><span class="sxs-lookup"><span data-stu-id="34a68-110">In the Facts Explorer window, click the **Vocabularies** tab.</span></span>  
  
2.  <span data-ttu-id="34a68-111">以滑鼠右鍵按一下**詞彙**資料夾，然後再按一下**新增詞彙**。</span><span class="sxs-lookup"><span data-stu-id="34a68-111">Right-click the **Vocabularies** folder, and then click **Add New Vocabulary**.</span></span>  
  
     <span data-ttu-id="34a68-112">新**詞彙**資料夾之下**詞彙**資料夾。</span><span class="sxs-lookup"><span data-stu-id="34a68-112">A new **vocabulary** folder appears under the **Vocabularies** folder.</span></span>  
  
3.  <span data-ttu-id="34a68-113">按一下新**詞彙**資料夾，然後再編輯 [屬性] 視窗中的名稱。</span><span class="sxs-lookup"><span data-stu-id="34a68-113">Click the new **vocabulary** folder, and then edit the name in the Properties window.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="34a68-114">您必須儲存所有項目 (定義的所有版本) 後，才能重新命名詞彙或原則。</span><span class="sxs-lookup"><span data-stu-id="34a68-114">You must save everything (all versions of the definitions) before you can rename a vocabulary or a policy.</span></span>