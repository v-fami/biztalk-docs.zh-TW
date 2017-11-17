---
title: "新增及移除命名空間中的 XML 訊息文件 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: dbf2f209-13b9-42e0-b0f2-b53ec705e84b
caps.latest.revision: "3"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: c3bb3b28504f92164aca1f66902546f1e04a2290
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="adding-and-removing-namespaces-in-an-xml-message-document"></a><span data-ttu-id="70b7b-102">新增及移除命名空間中的 XML 訊息文件</span><span class="sxs-lookup"><span data-stu-id="70b7b-102">Adding and Removing Namespaces in an XML Message Document</span></span>
<span data-ttu-id="70b7b-103">在此使用案例中，命名空間元件提供[!INCLUDE[esbToolkit](../includes/esbtoolkit-md.md)]將命名空間，或移除命名空間、 文件和訊息，如圖 1 所示。</span><span class="sxs-lookup"><span data-stu-id="70b7b-103">In this use case, the Namespace component provided with the [!INCLUDE[esbToolkit](../includes/esbtoolkit-md.md)] adds namespaces to, or removes namespaces from, documents and messages, as illustrated in Figure 1.</span></span> <span data-ttu-id="70b7b-104">這可避免命名空間衝突或文件會使用預設的命名空間時，所引發的錯誤。</span><span class="sxs-lookup"><span data-stu-id="70b7b-104">This prevents namespace clashes or errors arising when documents use default namespaces.</span></span>  
  
 <span data-ttu-id="70b7b-105">![新增/移除命名空間](../esb-toolkit/media/ch3-addingremovingnamespaces.gif "Ch3 AddingRemovingNamespaces")</span><span class="sxs-lookup"><span data-stu-id="70b7b-105">![Adding Removing Namespaces](../esb-toolkit/media/ch3-addingremovingnamespaces.gif "Ch3-AddingRemovingNamespaces")</span></span>  
  
 <span data-ttu-id="70b7b-106">**圖 1**</span><span class="sxs-lookup"><span data-stu-id="70b7b-106">**Figure 1**</span></span>  
  
 <span data-ttu-id="70b7b-107">**加入和移除 XML 文件和訊息的命名空間**</span><span class="sxs-lookup"><span data-stu-id="70b7b-107">**Adding and removing XML document and message namespaces**</span></span>  
  
 <span data-ttu-id="70b7b-108">命名空間元件 」 範例隨附[!INCLUDE[esbToolkit](../includes/esbtoolkit-md.md)]示範這個使用案例。</span><span class="sxs-lookup"><span data-stu-id="70b7b-108">The Namespace Component sample included with the [!INCLUDE[esbToolkit](../includes/esbtoolkit-md.md)] demonstrates this use case.</span></span> <span data-ttu-id="70b7b-109">它示範如何使用元件來插入及移除文件中的命名空間，做為傳送和接收程序的一部分。</span><span class="sxs-lookup"><span data-stu-id="70b7b-109">It shows how to use the component to inject and remove namespaces in a document as part of the send and the receive process.</span></span>  
  
 <span data-ttu-id="70b7b-110">如需詳細資訊，請參閱[安裝及執行 「 命名空間元件 」 範例](../esb-toolkit/installing-and-running-the-namespace-component-sample.md)。</span><span class="sxs-lookup"><span data-stu-id="70b7b-110">For more information, see [Installing and Running the Namespace Component Sample](../esb-toolkit/installing-and-running-the-namespace-component-sample.md).</span></span>