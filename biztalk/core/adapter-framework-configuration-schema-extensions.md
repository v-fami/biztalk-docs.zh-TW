---
title: "配接器架構組態結構描述延伸模組 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 27c9727f-5f97-41ee-a0b8-45d90427b0af
caps.latest.revision: "10"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 0cc50bcd592e104be0ffc82573c8ad9f4227858c
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="adapter-framework-configuration-schema-extensions"></a><span data-ttu-id="8d12f-102">配接器架構組態結構描述延伸模組</span><span class="sxs-lookup"><span data-stu-id="8d12f-102">Adapter Framework Configuration Schema Extensions</span></span>
<span data-ttu-id="8d12f-103">BizTalk 配接器架構支援根據 XSD 定義動態產生使用者介面。</span><span class="sxs-lookup"><span data-stu-id="8d12f-103">The BizTalk Adapter Framework supports the dynamic generation of user interfaces based on an XSD definition.</span></span> <span data-ttu-id="8d12f-104">配接器會提供必要的 XSD，而配接器架構則建立可讓使用者輸入值的屬性頁。</span><span class="sxs-lookup"><span data-stu-id="8d12f-104">The adapter supplies the required XSD and the Adapter Framework creates a property page that allows the user to enter values.</span></span>  
  
 <span data-ttu-id="8d12f-105">配接器架構會提供數個延伸模組，以便建立自訂使用者介面。</span><span class="sxs-lookup"><span data-stu-id="8d12f-105">To create custom user interfaces, the Adapter Framework provides several extensions.</span></span> <span data-ttu-id="8d12f-106">若要使用這些延伸模組，您必須匯入配接器架構結構描述 (BizTalkAdapterFramework.xsd)。</span><span class="sxs-lookup"><span data-stu-id="8d12f-106">To use these extensions, you must import the Adapter Framework schema (BizTalkAdapterFramework.xsd).</span></span> <span data-ttu-id="8d12f-107">藉由匯入結構描述，您便可以存取和使用配接器組態結構描述中的裝飾和特定類型。</span><span class="sxs-lookup"><span data-stu-id="8d12f-107">By importing the schema, you can access and use the decorations and specialized types in the adapter configuration schema.</span></span>  
  
 <span data-ttu-id="8d12f-108">使用本節所討論的裝飾標記和內建類型，以自訂配接器的屬性方格。</span><span class="sxs-lookup"><span data-stu-id="8d12f-108">Use the decoration tags and built-in types discussed in this section to customize the property grid for an adapter.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="8d12f-109">本節內容</span><span class="sxs-lookup"><span data-stu-id="8d12f-109">In This Section</span></span>  
  
-   [<span data-ttu-id="8d12f-110">啟用配接器架構組態延伸模組</span><span class="sxs-lookup"><span data-stu-id="8d12f-110">Enabling Adapter Framework Configuration Extensions</span></span>](../core/enabling-adapter-framework-configuration-extensions.md)  
  
-   [<span data-ttu-id="8d12f-111">配接器架構組態結構描述裝飾標記</span><span class="sxs-lookup"><span data-stu-id="8d12f-111">Adapter Framework Configuration Schema Decoration Tags</span></span>](../core/adapter-framework-configuration-schema-decoration-tags.md)  
  
-   [<span data-ttu-id="8d12f-112">自訂組態結構描述的配接器的範例</span><span class="sxs-lookup"><span data-stu-id="8d12f-112">Examples of Custom Configuration Schemas for Adapters</span></span>](../core/examples-of-custom-configuration-schemas-for-adapters.md)