---
title: 關於 HL7 標準 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- standards [HL7]
- HL7, standards
- Health Level Seven (HL7)
ms.assetid: 15f26ae3-d1ad-40a4-aafe-7148ef30cadb
caps.latest.revision: 3
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 9185248b5b897fbc7c909786c419b07fc3fb9d61
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22204838"
---
# <a name="about-the-hl7-standard"></a><span data-ttu-id="b69c6-102">關於 HL7 標準</span><span class="sxs-lookup"><span data-stu-id="b69c6-102">About the HL7 Standard</span></span>
<span data-ttu-id="b69c6-103">健全狀況層級七 (HL7) 標準的目的是協助醫療保健環境中的通訊。</span><span class="sxs-lookup"><span data-stu-id="b69c6-103">The purpose of the Health Level Seven (HL7) standard is to facilitate communication in health care environments.</span></span> <span data-ttu-id="b69c6-104">主要目標是提供醫療保健電腦刪除或大幅降低可能需要的自訂介面程式設計和程式維護的應用程式之間的資料交換標準。</span><span class="sxs-lookup"><span data-stu-id="b69c6-104">The primary goal is to provide standards for the exchange of data among health care computer applications that eliminate or substantially reduce the custom interface programming and program maintenance that may otherwise be required.</span></span> <span data-ttu-id="b69c6-105">您可以為目標的一組描述這個主要目標：</span><span class="sxs-lookup"><span data-stu-id="b69c6-105">You can delineate this primary goal as a set of goals:</span></span>  
  
-   <span data-ttu-id="b69c6-106">Standard 則支援各種技術的環境中實作的系統之間的交換。</span><span class="sxs-lookup"><span data-stu-id="b69c6-106">That the standard supports exchanges among systems implemented in the widest variety of technical environments.</span></span> <span data-ttu-id="b69c6-107">它的實作應該實際在各種不同的程式設計語言和作業系統。</span><span class="sxs-lookup"><span data-stu-id="b69c6-107">Its implementation should be practical in a wide variety of programming languages and operating systems.</span></span> <span data-ttu-id="b69c6-108">它也應該在各種不同的通訊環境中，範圍從完整的支援通訊 OSI 標準，七個層級網路 「 堆疊 」，比較不完整的環境，包括基本的點對點 RS 232 C connect 和傳送批次的媒體，例如磁碟和磁帶的資料。</span><span class="sxs-lookup"><span data-stu-id="b69c6-108">It should also support communications in a wide variety of communications environments, ranging from a full, OSI-compliant, seven level network "stack" to less complete environments, including primitive point-to-point RS 232C interconnections and transfer of data by batch media, such as floppy disk and tape.</span></span>  
  
-   <span data-ttu-id="b69c6-109">Standard 則支援單一交易以及檔案傳輸多個交易的立即傳送。</span><span class="sxs-lookup"><span data-stu-id="b69c6-109">That the standard supports immediate transfer of single transactions along with file transfers of multiple transactions.</span></span>  
  
-   <span data-ttu-id="b69c6-110">會在標準達到最大可能的標準化，與站台變化的使用方式和特定的資料元素的格式一致的程度。</span><span class="sxs-lookup"><span data-stu-id="b69c6-110">That the standard achieves the greatest possible degree of standardization, consistent with site variations in the usage and format of certain data elements.</span></span> <span data-ttu-id="b69c6-111">標準應該足以容納所需站台特有的變化。</span><span class="sxs-lookup"><span data-stu-id="b69c6-111">The standard should accommodate necessary site-specific variations.</span></span> <span data-ttu-id="b69c6-112">這包括，至少，站台特有的資料表、 程式碼定義，以及可能是站台特有的訊息區段 （例如，HL7 Z 區段）。</span><span class="sxs-lookup"><span data-stu-id="b69c6-112">This will include, at least, site-specific tables, code definitions, and possibly site-specific message segments (for example, HL7 Z segments).</span></span>  
  
-   <span data-ttu-id="b69c6-113">標準必須支援演化成長會辨識新的需求。</span><span class="sxs-lookup"><span data-stu-id="b69c6-113">That the standard must support evolutionary growth as new requirements are recognized.</span></span> <span data-ttu-id="b69c6-114">這包括支援的擴充功能和新發行簡介到現有的作業環境的程序。</span><span class="sxs-lookup"><span data-stu-id="b69c6-114">This includes support of the process of introducing extensions and new releases into existing operational environments.</span></span>  
  
-   <span data-ttu-id="b69c6-115">HL7 組織應該根據標準的經驗與現有的生產環境通訊協定和接受的業界標準通訊協定。</span><span class="sxs-lookup"><span data-stu-id="b69c6-115">That the HL7 organization should base the standard on experiences with existing production protocols and accepted industry-wide standard protocols.</span></span> <span data-ttu-id="b69c6-116">不過，標準不可能偏好的特定標準的其他使用者而妨礙公司專屬的興趣。</span><span class="sxs-lookup"><span data-stu-id="b69c6-116">However, the standard should not favor the proprietary interests of specific companies to the detriment of other users of the standard.</span></span> <span data-ttu-id="b69c6-117">同時，HL7 會嘗試保留個別的廠商可以將 marketplace 的唯一屬性。</span><span class="sxs-lookup"><span data-stu-id="b69c6-117">At the same time, HL7 seeks to preserve the unique attributes that an individual vendor can bring to the marketplace.</span></span>  
  
-   <span data-ttu-id="b69c6-118">雖然有用和相關專注於醫院中的資訊系統，標準的長期目標應該定義所有醫療保健環境中的格式和通訊協定，針對電腦應用程式。</span><span class="sxs-lookup"><span data-stu-id="b69c6-118">While it is both useful and pertinent to focus on information systems within hospitals, the long-term goal of the standard should be to define formats and protocols for computer applications in all health care environments.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="b69c6-119">本節內容</span><span class="sxs-lookup"><span data-stu-id="b69c6-119">In This Section</span></span>  
  
-   [<span data-ttu-id="b69c6-120">HL7 版本</span><span class="sxs-lookup"><span data-stu-id="b69c6-120">HL7 Versions</span></span>](../../adapters-and-accelerators/accelerator-hl7/hl7-versions.md)