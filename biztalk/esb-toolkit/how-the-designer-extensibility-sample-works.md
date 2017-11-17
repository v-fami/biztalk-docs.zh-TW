---
title: "設計工具擴充性範例的運作方式 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 8f4dc622-28b8-498d-961f-df969cff9dcb
caps.latest.revision: "2"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 74b72be8acb8fed465598814d2f76b32c6e3550d
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="how-the-designer-extensibility-sample-works"></a><span data-ttu-id="a9f03-102">設計工具擴充性範例的運作方式</span><span class="sxs-lookup"><span data-stu-id="a9f03-102">How the Designer Extensibility Sample Works</span></span>
<span data-ttu-id="a9f03-103">每個專案，在設計工具擴充性範例包含兩個類別： **Extender**類別和**擴充提供者**類別。</span><span class="sxs-lookup"><span data-stu-id="a9f03-103">Each project in the Designer Extensibility sample contains two classes: an **Extender** class and an **Extension Provider** class.</span></span> <span data-ttu-id="a9f03-104">這些類別設計用來擴充功能，以及定義屬性的**ItineraryDsl**模型項目。</span><span class="sxs-lookup"><span data-stu-id="a9f03-104">These classes are designed to extend the capabilities and define the properties of the **ItineraryDsl** model elements.</span></span>  
  
 <span data-ttu-id="a9f03-105">**擴充提供者**類別衍生自**ExtensionProviderBase**類別，並有**ExtensionProviderAttribute**套用這些屬性，找出擴充功能和其用途。</span><span class="sxs-lookup"><span data-stu-id="a9f03-105">The **Extension Provider** classes derive from the **ExtensionProviderBase** class and have the **ExtensionProviderAttribute** applied to them with properties that identify the extension and its purpose.</span></span> <span data-ttu-id="a9f03-106">這些值將顯示在設計工具中的使用者，當使用者正在設定**Extender**模型項目的屬性。</span><span class="sxs-lookup"><span data-stu-id="a9f03-106">These values will be displayed to the user in the designer when the user is setting the **Extender** property on a model element.</span></span> <span data-ttu-id="a9f03-107">當**擴充提供者**它們呼叫的建構函式的類別初始化**ExtensionProviderBase**並將擴充項類別的類型傳遞給它。</span><span class="sxs-lookup"><span data-stu-id="a9f03-107">When the **Extension Provider** classes initialize, they call to the constructor for the **ExtensionProviderBase** and pass to it the type of the extender class.</span></span>  
  
 <span data-ttu-id="a9f03-108">**Extender**類別具有**ObjectExtender**屬性套用至它們; 若要**ObjectExtender**屬性，傳遞中物件的型別**ItineraryDsl**它們所擴充。</span><span class="sxs-lookup"><span data-stu-id="a9f03-108">The **Extender** classes have an **ObjectExtender** attribute applied to them; to the **ObjectExtender** attribute, they pass the type of the object in the **ItineraryDsl** that they extend.</span></span> <span data-ttu-id="a9f03-109">這些類別的基底類別會因擴充項的類型而異。</span><span class="sxs-lookup"><span data-stu-id="a9f03-109">The base class for these classes varies, depending on the type of extender.</span></span> <span data-ttu-id="a9f03-110">基底類別的解析程式 extender **ObjectExtender\<解析程式 >**。</span><span class="sxs-lookup"><span data-stu-id="a9f03-110">For Resolver extenders, the base class is **ObjectExtender\<Resolver>**.</span></span> <span data-ttu-id="a9f03-111">路線服務的擴充項的基底類別是**ItineraryServiceExtenderBase**。</span><span class="sxs-lookup"><span data-stu-id="a9f03-111">For Itinerary Service extenders, the base class is **ItineraryServiceExtenderBase**.</span></span> <span data-ttu-id="a9f03-112">在**Extender**類別，下列屬性會套用至屬性： 所需的正確地顯示在屬性方格中，屬性進行驗證時，Microsoft 企業程式庫中包含屬性所需的適當的序列化屬性和/或屬性，以決定如何保存內容。</span><span class="sxs-lookup"><span data-stu-id="a9f03-112">In the **Extender** classes, the following attributes are applied to the properties: attributes necessary for proper display in a property grid, attributes included in the Microsoft Enterprise Library for validation purposes, attributes necessary for proper serialization, and/or attributes that determine how properties are persisted.</span></span>  
  
 <span data-ttu-id="a9f03-113">當這些組件，編譯並放置在 Lib 資料夾中時，載入及快取設計工具在執行階段。</span><span class="sxs-lookup"><span data-stu-id="a9f03-113">When these assemblies are compiled and placed in the Lib folder, they are loaded and cached by the designer at run time.</span></span> <span data-ttu-id="a9f03-114">視需要擴充項**ItineraryDsl**使用反映來從快取載入適用的組件，藉由檢查匯出之型別的和在這些類型的屬性。</span><span class="sxs-lookup"><span data-stu-id="a9f03-114">As extenders are needed, the **ItineraryDsl** uses reflection to load the applicable assemblies from the cache by examining the types exported and the attributes on those types.</span></span>