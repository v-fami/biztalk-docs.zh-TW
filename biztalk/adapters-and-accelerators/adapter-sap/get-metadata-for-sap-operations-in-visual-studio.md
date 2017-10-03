---
title: "取得 Visual Studio 中的 SAP 作業的中繼資料 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: metadata, retrieving for SAP operations in Visual Studio
ms.assetid: 1be5934a-a5d4-4734-8bea-fb8274f59c71
caps.latest.revision: "7"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: e5c786ea9b1acbc3ed88c79187725697ce279ea5
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="get-metadata-for-sap-operations-in-visual-studio"></a><span data-ttu-id="8ef66-102">取得 Visual Studio 中的 SAP 作業的中繼資料</span><span class="sxs-lookup"><span data-stu-id="8ef66-102">Get Metadata for SAP Operations in Visual Studio</span></span>
<span data-ttu-id="8ef66-103">[!INCLUDE[adaptersap](../../includes/adaptersap-md.md)]提供兩個[!INCLUDE[btsVStudioNoVersion](../../includes/btsvstudionoversion-md.md)]可用來協助您開發解決方案使用配接器的元件 — [!INCLUDE[consumeadapterservlong](../../includes/consumeadapterservlong-md.md)]、 [!INCLUDE[addadapterwiz](../../includes/addadapterwiz-md.md)]，而[!INCLUDE[addadapterservrefshort](../../includes/addadapterservrefshort-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="8ef66-103">The [!INCLUDE[adaptersap](../../includes/adaptersap-md.md)] provides two [!INCLUDE[btsVStudioNoVersion](../../includes/btsvstudionoversion-md.md)] components that you can use to help you develop solutions using the adapter—the [!INCLUDE[consumeadapterservlong](../../includes/consumeadapterservlong-md.md)], the [!INCLUDE[addadapterwiz](../../includes/addadapterwiz-md.md)], and the [!INCLUDE[addadapterservrefshort](../../includes/addadapterservrefshort-md.md)].</span></span> <span data-ttu-id="8ef66-104">配接器用戶端必須使用這些元件，來連接至 SAP 系統，並產生 SAP 成品他們想要叫用的中繼資料。</span><span class="sxs-lookup"><span data-stu-id="8ef66-104">Adapter clients must use these components to connect to an SAP system and then generate metadata for the SAP artifacts they want to invoke.</span></span>  
  
 <span data-ttu-id="8ef66-105">所有這些[!INCLUDE[btsVStudioNoVersion](../../includes/btsvstudionoversion-md.md)]元件簡化開發：</span><span class="sxs-lookup"><span data-stu-id="8ef66-105">All these [!INCLUDE[btsVStudioNoVersion](../../includes/btsvstudionoversion-md.md)] components simplify development by:</span></span>  
  
-   <span data-ttu-id="8ef66-106">提供的 Microsoft Windows 介面，您可以瀏覽和搜尋您想要使用您的方案中的作業。</span><span class="sxs-lookup"><span data-stu-id="8ef66-106">Providing a Microsoft Windows interface through which you can browse and search for operations that you want to use in your solution.</span></span>  
  
-   <span data-ttu-id="8ef66-107">正在擷取這些目標作業的配接器所公開的中繼資料。</span><span class="sxs-lookup"><span data-stu-id="8ef66-107">Retrieving metadata exposed by the adapter for these target operations.</span></span>  
  
-   <span data-ttu-id="8ef66-108">轉換的中繼資料，這表示做為 Web 服務描述語言 (WSDL) 文件，配接器，成您可以使用您的方案 （BizTalk 專案的 XSD 訊息結構描述或 WCF 服務合約的.NET 物件表示法中的表單服務模型） 並將它加入至您的專案。</span><span class="sxs-lookup"><span data-stu-id="8ef66-108">Converting that metadata, which is expressed as a Web Services Description Language (WSDL) document by the adapter, into a form that you can use in your solution (XSD message schemas for BizTalk projects or a .NET object representation of a service contract for the WCF service model) and adding it to your project.</span></span>  
  
 <span data-ttu-id="8ef66-109">本節提供有關如何使用指示[!INCLUDE[consumeadapterservshort](../../includes/consumeadapterservshort-md.md)]、 [!INCLUDE[addadapterwiz](../../includes/addadapterwiz-md.md)]，而[!INCLUDE[addadapterservrefshort](../../includes/addadapterservrefshort-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="8ef66-109">This section provides instructions about how to use the [!INCLUDE[consumeadapterservshort](../../includes/consumeadapterservshort-md.md)], the [!INCLUDE[addadapterwiz](../../includes/addadapterwiz-md.md)], and the [!INCLUDE[addadapterservrefshort](../../includes/addadapterservrefshort-md.md)].</span></span>  
  
 
  
## <a name="see-also"></a><span data-ttu-id="8ef66-110">另請參閱</span><span class="sxs-lookup"><span data-stu-id="8ef66-110">See Also</span></span>  
[<span data-ttu-id="8ef66-111">開發您的 SAP 應用程式</span><span class="sxs-lookup"><span data-stu-id="8ef66-111">Develop your SAP applications</span></span>](../../adapters-and-accelerators/adapter-sap/develop-your-sap-applications.md)