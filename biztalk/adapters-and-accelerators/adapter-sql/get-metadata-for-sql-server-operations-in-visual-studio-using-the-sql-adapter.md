---
title: 取得在 Visual Studio 中使用 SQL 配接器的 SQL Server 作業的中繼資料 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 5a7ac720-e573-4564-8d15-8212a815f1f7
caps.latest.revision: 8
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 2e9b8b7ab1d1cf8a0223756ae5fe7cacaf154750
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "37010751"
---
# <a name="get-metadata-for-sql-server-operations-in-visual-studio-using-the-sql-adapter"></a><span data-ttu-id="f325b-102">取得在 Visual Studio 中使用 SQL 配接器的 SQL Server 作業的中繼資料</span><span class="sxs-lookup"><span data-stu-id="f325b-102">Get metadata for SQL Server operations in Visual Studio using the SQL adapter</span></span>
<span data-ttu-id="f325b-103">[!INCLUDE[adaptersql](../../includes/adaptersql-md.md)]提供三個[!INCLUDE[btsVStudioNoVersion](../../includes/btsvstudionoversion-md.md)]可用來協助您開發解決方案使用配接器的元件 — [!INCLUDE[consumeadapterservlong](../../includes/consumeadapterservlong-md.md)]，則[!INCLUDE[addadapterwiz](../../includes/addadapterwiz-md.md)]，和[!INCLUDE[addadapterservreflong](../../includes/addadapterservreflong-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="f325b-103">The [!INCLUDE[adaptersql](../../includes/adaptersql-md.md)] provides three [!INCLUDE[btsVStudioNoVersion](../../includes/btsvstudionoversion-md.md)] components that you can use to help you develop solutions using the adapter—the [!INCLUDE[consumeadapterservlong](../../includes/consumeadapterservlong-md.md)], the [!INCLUDE[addadapterwiz](../../includes/addadapterwiz-md.md)], and the [!INCLUDE[addadapterservreflong](../../includes/addadapterservreflong-md.md)].</span></span> <span data-ttu-id="f325b-104">配接器用戶端必須使用這些元件來連接到 SQL Server，然後再產生在想要執行作業的中繼資料。</span><span class="sxs-lookup"><span data-stu-id="f325b-104">Adapter clients must use these components to connect to SQL Server and then generate metadata for the operations they want to perform.</span></span>  
  
 <span data-ttu-id="f325b-105">所有這些[!INCLUDE[btsVStudioNoVersion](../../includes/btsvstudionoversion-md.md)]元件簡化開發：</span><span class="sxs-lookup"><span data-stu-id="f325b-105">All these [!INCLUDE[btsVStudioNoVersion](../../includes/btsvstudionoversion-md.md)] components simplify development by:</span></span>  
  
- <span data-ttu-id="f325b-106">提供的 Microsoft Windows 介面，您可以透過它瀏覽，然後搜尋您想要使用您的方案中的作業。</span><span class="sxs-lookup"><span data-stu-id="f325b-106">Providing a Microsoft Windows interface through which you can browse and search for operations that you want to use in your solution.</span></span>  
  
- <span data-ttu-id="f325b-107">正在擷取這些目標作業的配接器所公開的中繼資料。</span><span class="sxs-lookup"><span data-stu-id="f325b-107">Retrieving metadata exposed by the adapter for these target operations.</span></span>  
  
- <span data-ttu-id="f325b-108">轉換該中繼資料，這會以 Web 服務描述語言 (WSDL) 文件，配接器，成您可以使用您的解決方案 （BizTalk 專案的 XSD 訊息結構描述或針對 WCF 服務合約的.NET 物件表示法中的表單服務模型） 並將它新增至您的專案。</span><span class="sxs-lookup"><span data-stu-id="f325b-108">Converting that metadata, which is expressed as a Web Services Description Language (WSDL) document by the adapter, into a form that you can use in your solution (XSD message schemas for BizTalk projects or a .NET object representation of a service contract for the WCF service model) and adding it to your project.</span></span>  
  
  <span data-ttu-id="f325b-109">本節提供有關如何使用指示[!INCLUDE[consumeadapterservshort](../../includes/consumeadapterservshort-md.md)]，則[!INCLUDE[addadapterwiz](../../includes/addadapterwiz-md.md)]，和[!INCLUDE[addadapterservrefshort](../../includes/addadapterservrefshort-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="f325b-109">This section provides instructions about how to use the [!INCLUDE[consumeadapterservshort](../../includes/consumeadapterservshort-md.md)], the [!INCLUDE[addadapterwiz](../../includes/addadapterwiz-md.md)], and the [!INCLUDE[addadapterservrefshort](../../includes/addadapterservrefshort-md.md)].</span></span>  
  
