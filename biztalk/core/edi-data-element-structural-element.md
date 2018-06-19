---
title: EDI 資料項目結構元素 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 775e8b87-b952-46d2-a506-5174d216a9aa
caps.latest.revision: 6
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 600edb30ff157a520ac67eebce58428a62e27c8e
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22239470"
---
# <a name="edi-data-element-structural-element"></a><span data-ttu-id="38c50-102">EDI 資料項目結構元素</span><span class="sxs-lookup"><span data-stu-id="38c50-102">EDI Data Element Structural Element</span></span>
<span data-ttu-id="38c50-103">這種資料元素是訊息中的主要資料單位。</span><span class="sxs-lookup"><span data-stu-id="38c50-103">The data element is the primary unit of data in the message.</span></span> <span data-ttu-id="38c50-104">資料元素分隔的資料元素分隔符號，也就是星號，根據預設，對於 X12 和 EDIFACT 的預設值加上加號。</span><span class="sxs-lookup"><span data-stu-id="38c50-104">Data elements are separated by the data element separator, which is an asterisk by default for X12 and a plus sign by default for EDIFACT.</span></span> <span data-ttu-id="38c50-105">資料元素的選用性分為強制性、選用性或條件性。</span><span class="sxs-lookup"><span data-stu-id="38c50-105">The optionality of data elements is defined as mandatory, optional, or conditional.</span></span>  
  
 <span data-ttu-id="38c50-106">資料元素可以是簡單或複合。</span><span class="sxs-lookup"><span data-stu-id="38c50-106">A data element can be either simple or composite.</span></span> <span data-ttu-id="38c50-107">簡單資料元素為數字形式，屬於最低層的資料。</span><span class="sxs-lookup"><span data-stu-id="38c50-107">Simple data elements are numeric and are the lowest level of data.</span></span> <span data-ttu-id="38c50-108">複合資料元素為的子元素，這是由元件分隔符號隔開的簡單資料元素的串連。</span><span class="sxs-lookup"><span data-stu-id="38c50-108">Composite data elements are concatenations of sub element, which are simple data elements separated by a component separator.</span></span> <span data-ttu-id="38c50-109">根據預設，元件分隔符號是 X12 和 EDIFACT 的冒號。</span><span class="sxs-lookup"><span data-stu-id="38c50-109">By default, the component separator is the colon for X12 and EDIFACT.</span></span>  
  
 <span data-ttu-id="38c50-110">對於 EDIFACT 編碼訊息，如果要透過 EDI 傳送的資料需要傳送任何字元，定義用來做為分隔符號，您需要使用釋放字元表示接的字元不是為分隔符號，而是資料的一部分。</span><span class="sxs-lookup"><span data-stu-id="38c50-110">For EDIFACT-encoded messages, if the data to be sent via EDI needs to send any character defined for use as a separator, you need to use a release character to indicate that the following character is not a separator, but is part of the data.</span></span> <span data-ttu-id="38c50-111">預設的釋放字元為問號 (?)。</span><span class="sxs-lookup"><span data-stu-id="38c50-111">The release character is by default the question mark (?).</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="38c50-112">X12 不支援釋放字元。</span><span class="sxs-lookup"><span data-stu-id="38c50-112">A release character is not supported for X12.</span></span> <span data-ttu-id="38c50-113">如果 X12 編碼交換資料中出現分隔符號，無論在接收端或是傳送端，該交換都會遭到擱置。</span><span class="sxs-lookup"><span data-stu-id="38c50-113">If a separator is encountered as part of the data of an X12-encoded interchange, on either the receive or send side, the interchange will be suspended.</span></span>