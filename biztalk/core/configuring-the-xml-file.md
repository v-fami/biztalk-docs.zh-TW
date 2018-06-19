---
title: 設定 XML 檔案 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 52851901-8374-412f-9c29-83845d8d4861
caps.latest.revision: 4
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 4d791de9b6fe90ebb850874026e8d52e49732f32
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22233822"
---
# <a name="configuring-the-xml-file"></a><span data-ttu-id="e5cc4-102">設定 XML 檔案</span><span class="sxs-lookup"><span data-stu-id="e5cc4-102">Configuring the XML File</span></span>
<span data-ttu-id="e5cc4-103">當您安裝「企業單一登入」(SSO) 時，名為 ENTSSO.xml 的 XML 檔案會安裝在 Extensions 目錄中。</span><span class="sxs-lookup"><span data-stu-id="e5cc4-103">When you install Enterprise Single Sign-On (SSO), an XML file named ENTSSO.xml is installed in your Extensions directory.</span></span> <span data-ttu-id="e5cc4-104">您可以編輯這個檔案，定義 ENTSSO「管理代理程式」(MA) 所有執行個體的組態。</span><span class="sxs-lookup"><span data-stu-id="e5cc4-104">By editing the file, you define the configuration for all instances of the ENTSSO Management Agent (MA).</span></span>  
  
 <span data-ttu-id="e5cc4-105">這個檔案看起來類似如下：</span><span class="sxs-lookup"><span data-stu-id="e5cc4-105">The file is similar to the following:</span></span>  
  
```  
<?xml version="1.0" encoding="utf-8"?>  
<sso>  
  
  <SourceMA name="RACFMA1" objectType="person" attribute="uid"/>  
  <SourceMA name="ACF2" objectType="person" attribute="uid"/>  
  
  <ENTSSOMA name ="ENTSSOMA1" adma="ADMA1" deleteAll="true">  
    <Application name="AppForRACF1A" sourceMA="RACFMA1" create="true" delete="true"/>  
    <Application name="AppForRACF1B" sourceMA="RACFMA1" create="true" delete="false"/>  
  </ENTSSOMA>  
  
  <ENTSSOMA name ="ENTSSOMA2" adma="ADMA1" deleteAll="true">  
    <Application name="AppForACF2" sourceMA="ACF2"/>  
  </ENTSSOMA>  
  
</sso>  
```  
  
## <a name="xml-elements-and-attributes"></a><span data-ttu-id="e5cc4-106">XML 項目和屬性</span><span class="sxs-lookup"><span data-stu-id="e5cc4-106">XML Elements and Attributes</span></span>  
 <span data-ttu-id="e5cc4-107">下列清單說明 XML 檔案中定義的項目和屬性。</span><span class="sxs-lookup"><span data-stu-id="e5cc4-107">The following list describes the elements and attributes that you define in the XML file.</span></span> <span data-ttu-id="e5cc4-108">請注意，這個檔案中的所有項目和屬性都區分大小寫。</span><span class="sxs-lookup"><span data-stu-id="e5cc4-108">Note that all element and attribute names in this file are case sensitive.</span></span>  
  
 <span data-ttu-id="e5cc4-109">**項目： ENTSSO** -定義單一 ENTSSO MA 執行個體的組態。</span><span class="sxs-lookup"><span data-stu-id="e5cc4-109">**Element: ENTSSO** - Defines the configuration of a single ENTSSO MA instance.</span></span> <span data-ttu-id="e5cc4-110">允許有多個 ENTSSO 項目。</span><span class="sxs-lookup"><span data-stu-id="e5cc4-110">Multiple ENTSSO elements are allowed.</span></span>  
  
 <span data-ttu-id="e5cc4-111">**屬性： 名稱**-定義 ENTSSO 管理代理程式的執行個體名稱，而且必須符合 ENTSSO 管理代理程式執行個體中 Microsoft Identity Integration Server (MIIS) 的名稱。</span><span class="sxs-lookup"><span data-stu-id="e5cc4-111">**Attribute: name** - Defines the instance name of the ENTSSO Management Agent, and must match the name of the ENTSSO Management Agent instance in Microsoft Identity Integration Server (MIIS).</span></span>  
  
 <span data-ttu-id="e5cc4-112">**屬性： adma** -定義 ENTSSO 管理代理程式執行個體將會使用 Active Directory 管理代理程式的執行個體名稱。</span><span class="sxs-lookup"><span data-stu-id="e5cc4-112">**Attribute: adma** - Defines the instance name of the Active Directory Management Agent that will be used by this ENTSSO Management Agent instance.</span></span> <span data-ttu-id="e5cc4-113">Active Directory「管理代理程式」可提供 Windows 網域名稱和 Windows 使用者名稱以供對應。</span><span class="sxs-lookup"><span data-stu-id="e5cc4-113">The Active Directory Management Agent provides the Windows domain name and Windows user name for the mapping.</span></span> <span data-ttu-id="e5cc4-114">這個 Active Directory「管理代理程式」執行個體名稱必須與 MIIS 中的 Active Directory「管理代理程式」執行個體名稱相符。</span><span class="sxs-lookup"><span data-stu-id="e5cc4-114">This Active Directory Management Agent instance name must match the name of an Active Directory Management Agent instance in MIIS.</span></span>  
  
 <span data-ttu-id="e5cc4-115">**屬性： deleteAll** -選擇項，預設值是`true`。</span><span class="sxs-lookup"><span data-stu-id="e5cc4-115">**Attribute: deleteAll** - Optional; default is `true`.</span></span> <span data-ttu-id="e5cc4-116">若此屬性設定為 `true`，則刪除某個 Windows 識別時，該 Windows 識別的所有對應都將會從所有 ENTSSO 應用程式中刪除。</span><span class="sxs-lookup"><span data-stu-id="e5cc4-116">If this is set to `true`, and a Windows identity is deleted, all mappings with that Windows identity are deleted from all ENTSSO applications.</span></span>  
  
 <span data-ttu-id="e5cc4-117">**項目： 應用程式**-定義 SSO 分支機構應用程式和外部的管理代理程式之間的關聯性。</span><span class="sxs-lookup"><span data-stu-id="e5cc4-117">**Element: Application** - Defines the relationship between an SSO affiliate application and an external Management Agent.</span></span> <span data-ttu-id="e5cc4-118">允許有多個 `Application` 項目。</span><span class="sxs-lookup"><span data-stu-id="e5cc4-118">Multiple `Application` elements are allowed.</span></span>  
  
 <span data-ttu-id="e5cc4-119">**屬性： 名稱**-定義 SSO 分支機構應用程式的名稱。</span><span class="sxs-lookup"><span data-stu-id="e5cc4-119">**Attribute: name** - Defines the name of the SSO affiliate application.</span></span> <span data-ttu-id="e5cc4-120">這個應用程式必須已經存在於 ENTSSO 系統內。</span><span class="sxs-lookup"><span data-stu-id="e5cc4-120">This application must already exist within the ENTSSO system.</span></span>  
  
 <span data-ttu-id="e5cc4-121">**屬性： sourceMA** -定義來源 （外部） 的執行個體名稱將用來提供此應用程式的對應中的外部 UserId 的管理代理程式。</span><span class="sxs-lookup"><span data-stu-id="e5cc4-121">**Attribute: sourceMA** - Defines the instance name for the source (external) Management Agent that will be used to provide the external UserId in the mapping for this application.</span></span> <span data-ttu-id="e5cc4-122">這個外部「管理代理程式」執行個體名稱必須與 MIIS 中的外部 MA 執行個體名稱相符。</span><span class="sxs-lookup"><span data-stu-id="e5cc4-122">This external Management Agent instance name must match the name of an external MA instance in MIIS.</span></span>  
  
 <span data-ttu-id="e5cc4-123">**屬性： 建立**-選擇項，預設值是`true`。</span><span class="sxs-lookup"><span data-stu-id="e5cc4-123">**Attribute: create** - Optional; default is `true`.</span></span> <span data-ttu-id="e5cc4-124">此屬性會定義是否應該為這個應用程式建立對應。</span><span class="sxs-lookup"><span data-stu-id="e5cc4-124">Defines whether mappings should be created for this application.</span></span>  
  
 <span data-ttu-id="e5cc4-125">**屬性： 刪除**-選擇項，預設值是`true`。</span><span class="sxs-lookup"><span data-stu-id="e5cc4-125">**Attribute: delete** - Optional; default is `true`.</span></span> <span data-ttu-id="e5cc4-126">此屬性會定義是否應該為這個應用程式刪除對應。</span><span class="sxs-lookup"><span data-stu-id="e5cc4-126">Defines whether mappings should be deleted for this application.</span></span>  
  
 <span data-ttu-id="e5cc4-127">**項目： SourceMA** -選擇性。</span><span class="sxs-lookup"><span data-stu-id="e5cc4-127">**Element: SourceMA** - Optional.</span></span> <span data-ttu-id="e5cc4-128">此項目會識別特定來源 (外部)「管理代理程式」執行個體的物件類型和屬性名稱。</span><span class="sxs-lookup"><span data-stu-id="e5cc4-128">Identifies the object type and attribute names for a specific source (external) Management Agent instance.</span></span> <span data-ttu-id="e5cc4-129">如果特定「管理代理程式」沒有這個項目，則會假設為預設物件類型 (“person”) 和屬性名稱 (“uid”)。</span><span class="sxs-lookup"><span data-stu-id="e5cc4-129">If this element is not present for a specific Management Agent, then the default object type (“person”) and attribute names (“uid”) are assumed.</span></span> <span data-ttu-id="e5cc4-130">允許有多個 `SourceMA` 項目。</span><span class="sxs-lookup"><span data-stu-id="e5cc4-130">Multiple `SourceMA` elements are allowed.</span></span>  
  
 <span data-ttu-id="e5cc4-131">**屬性： 名稱**-來源 （外部） 的名稱管理代理程式。</span><span class="sxs-lookup"><span data-stu-id="e5cc4-131">**Attribute: name** - The name of the source (external) Management Agent.</span></span> <span data-ttu-id="e5cc4-132">這個名稱必須至少符合 `sourceMA` 項目的其中一個 `Application` 屬性名稱。</span><span class="sxs-lookup"><span data-stu-id="e5cc4-132">This name must match at least one of the `sourceMA` attribute names from the `Application` elements.</span></span>  
  
 <span data-ttu-id="e5cc4-133">**屬性： objectType** -選擇項，預設值是`person`。</span><span class="sxs-lookup"><span data-stu-id="e5cc4-133">**Attribute: objectType** - Optional; default is `person`.</span></span> <span data-ttu-id="e5cc4-134">如果提供外部 UserId 的物件類型名稱不是 `person`，則應在此指定。</span><span class="sxs-lookup"><span data-stu-id="e5cc4-134">If the object type name that provides the external UserId is not `person`, it should be specified here.</span></span>  
  
 <span data-ttu-id="e5cc4-135">**屬性： 屬性**-選擇項，預設值是`uid`。</span><span class="sxs-lookup"><span data-stu-id="e5cc4-135">**Attribute: attribute** - Optional; default is `uid`.</span></span> <span data-ttu-id="e5cc4-136">如果提供外部 UserId 的屬性名稱不是 `uid`，則可以在此指定。</span><span class="sxs-lookup"><span data-stu-id="e5cc4-136">If the attribute name that provides the external UserId is not `uid`, you can specify it here.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e5cc4-137">另請參閱</span><span class="sxs-lookup"><span data-stu-id="e5cc4-137">See Also</span></span>  
 [<span data-ttu-id="e5cc4-138">如何使用 ENTSSO 管理代理程式</span><span class="sxs-lookup"><span data-stu-id="e5cc4-138">How to Use the ENTSSO Management Agent</span></span>](../core/how-to-use-the-entsso-management-agent.md)