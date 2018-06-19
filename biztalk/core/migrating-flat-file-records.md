---
title: 移轉一般檔案記錄 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 75cd5fbc-66c1-4c8b-b81a-1d028e9647b4
caps.latest.revision: 9
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: ddd43c231077f4e23efca374edbda5bf152f1415
ms.sourcegitcommit: 32f380810b90b70e5df7be72a6a14988a747868e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/28/2018
ms.locfileid: "29710817"
---
# <a name="migrate-flat-file-records"></a><span data-ttu-id="289c6-102">移轉一般檔案記錄</span><span class="sxs-lookup"><span data-stu-id="289c6-102">Migrate Flat File Records</span></span>

## <a name="overview"></a><span data-ttu-id="289c6-103">概觀</span><span class="sxs-lookup"><span data-stu-id="289c6-103">Overview</span></span>
<span data-ttu-id="289c6-104">Microsoft BizTalk Server 可支援多字元的分隔符號，雖然它支援只有一種分隔符號類型 — 子分隔符號。</span><span class="sxs-lookup"><span data-stu-id="289c6-104">Microsoft BizTalk Server supports multi-character delimiters, although it supports only one type of delimiter—child delimiter.</span></span> 
  
 <span data-ttu-id="289c6-105">三個結構描述註解會控制分隔符號的 BizTalk Server 中的處理： 兩個供剖析 (**skip_CR**， **skip_LF**)，一種與序列化 (**append_newline**)。</span><span class="sxs-lookup"><span data-stu-id="289c6-105">Three schema annotations control delimiter handling in BizTalk Server: two for parsing (**skip_CR**, **skip_LF**), and one for serializing (**append_newline**).</span></span> <span data-ttu-id="289c6-106">BizTalk Server 會解譯這些註解，如下所示在移轉記錄時：</span><span class="sxs-lookup"><span data-stu-id="289c6-106">BizTalk Server interprets these annotations as follows when migrating records:</span></span>  
  
-   <span data-ttu-id="289c6-107">如果**skip_CR**註釋的值為**true**和目前的分隔符號不是歸位字元 (0x0D)，BizTalk Server 會將歸位字元新增到目前的分隔符號。</span><span class="sxs-lookup"><span data-stu-id="289c6-107">If the **skip_CR** annotation has a value of **true** and the current delimiter is not carriage return (0x0D), BizTalk Server adds a carriage return to the current delimiter.</span></span> <span data-ttu-id="289c6-108">例如，若目前的分隔符號是縱線符號 (0x7C)，則產生的分隔符號是縱線符號，後面接著歸位字元 (0x7C 0x0D)。</span><span class="sxs-lookup"><span data-stu-id="289c6-108">For example, if the current delimiter were the pipe symbol (0x7C), the resulting delimiter is a pipe symbol followed by a carriage return (0x7C 0x0D).</span></span> <span data-ttu-id="289c6-109">如果目前的分隔符號是歸位字元，它會保持為單一歸位字元的值為何 **skip_CR**。</span><span class="sxs-lookup"><span data-stu-id="289c6-109">If the current delimiter is carriage return, it remains as a single carriage return regardless of the value of **skip_CR**.</span></span>  
  
-   <span data-ttu-id="289c6-110">如果**skip_LF**註釋的值為**true**，BizTalk Server 會將換行字元 （0x0a） 新增到目前的分隔符號。</span><span class="sxs-lookup"><span data-stu-id="289c6-110">If the **skip_LF** annotation has a value of **true**, BizTalk Server adds a linefeed character (0x0A) to the current delimiter.</span></span> <span data-ttu-id="289c6-111">請注意，上述情況中，目前的分隔符號是縱線符號 (0x7C)，在三個字元會產生 (0x7C 0x0D 0x0A) 如果這兩個 **skip_CR** 和 **skip_LF** 是 **true**。</span><span class="sxs-lookup"><span data-stu-id="289c6-111">Notice that in the preceding case where the current delimiter is the pipe symbol (0x7C), a three character delimiter results (0x7C 0x0D 0x0A) if both **skip_CR** and **skip_LF** are **true**.</span></span>  
  
-   <span data-ttu-id="289c6-112">BizTalk Server 會略過的設定**append_newline**註解。</span><span class="sxs-lookup"><span data-stu-id="289c6-112">BizTalk Server ignores the setting of the **append_newline** annotation.</span></span>  
  
 <span data-ttu-id="289c6-113">雖然這些註解的解譯可確保大部分的情況順利移轉，但是在某些情況下，會發生移轉失敗。</span><span class="sxs-lookup"><span data-stu-id="289c6-113">While these interpretations of the annotations ensure the majority of cases migrate without difficulty, there are some cases where migration fails.</span></span> <span data-ttu-id="289c6-114">例如，如果**skip_CR**和**skip_LF**都**true**和目前的分隔符號是縱線符號 (0x7C)，BizTalk Server 可接受下列為有效的所有在一組的記錄中的分隔符號： 0x7C 0x0D 0x0A、 0x7C 0x0D、 0x7c 0x0a 以及 0x7C。</span><span class="sxs-lookup"><span data-stu-id="289c6-114">For example, if **skip_CR** and **skip_LF** are both **true** and the current delimiter is the pipe symbol (0x7C), BizTalk Server accepts all of the following as valid delimiters within a single set of records: 0x7C 0x0D 0x0A, 0x7C 0x0D, 0x7C 0x0A, and 0x7C.</span></span> <span data-ttu-id="289c6-115">使用這類分隔符號集的記錄無法移轉，且需要自訂剖析器在 BizTalk Server 中的程式碼。</span><span class="sxs-lookup"><span data-stu-id="289c6-115">Records using such sets of delimiters cannot be migrated and require custom parser code in BizTalk Server.</span></span>  
  
 <span data-ttu-id="289c6-116">雖然 BizTalk Server 只一種分隔符號類型，它可解譯舊版註解，以便輕鬆地移轉記錄。</span><span class="sxs-lookup"><span data-stu-id="289c6-116">Although BizTalk Server has only one type of delimiter, it interprets the old annotations so that records migrate easily.</span></span> <span data-ttu-id="289c6-117">如果 BizTalk Server 結構描述具有值**def_record_delimdef_field_delim**， **def_subfield_delim**，在中參考這些**delimiter_type**為**inherit_record**，依此類推，BizTalk Server 擷取對應的值，並將它儲存在本機。</span><span class="sxs-lookup"><span data-stu-id="289c6-117">If a BizTalk Server schema has values for **def_record_delimdef_field_delim**, **def_subfield_delim**, and these are referenced in **delimiter_type** as **inherit_record**, and so on, BizTalk Server retrieves the corresponding value and stores it locally.</span></span>  
  
 <span data-ttu-id="289c6-118">此外，BizTalk Server 新增為子系已標記位置記錄的欄位。</span><span class="sxs-lookup"><span data-stu-id="289c6-118">In addition, BizTalk Server adds fields for tagged positional records without children.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="289c6-119">另請參閱</span><span class="sxs-lookup"><span data-stu-id="289c6-119">See Also</span></span>  
 [<span data-ttu-id="289c6-120">產生和驗證結構描述的已知問題</span><span class="sxs-lookup"><span data-stu-id="289c6-120">Known Issues with Schema Generation and Validation</span></span>](../core/known-issues-with-schema-generation-and-validation.md)