---
title: SendPortCollection 節點 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- SendPortCollection node [binding file]
ms.assetid: 2084507e-ef70-4828-a15f-51d676b14333
caps.latest.revision: 7
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: d2cf0a968ef995bfdb5a551d16b204743d507b25
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="sendportcollection-node"></a><span data-ttu-id="67662-102">SendPortCollection 節點</span><span class="sxs-lookup"><span data-stu-id="67662-102">SendPortCollection Node</span></span>
<span data-ttu-id="67662-103">繫結檔案的 SendPortCollection 節點是所有 SendPort 節點的父節點，這些節點包含隨同繫結檔案一起匯出之傳送埠的特定相關資訊。</span><span class="sxs-lookup"><span data-stu-id="67662-103">The SendPortCollection node of a binding file is the parent node for all of the SendPort nodes which contain specific information about a send port that is exported with the binding file.</span></span>  
  
## <a name="nodes-in-the-sendportcollection-node"></a><span data-ttu-id="67662-104">SendPortCollection 節點中的節點</span><span class="sxs-lookup"><span data-stu-id="67662-104">Nodes in the SendPortCollection node</span></span>  
 <span data-ttu-id="67662-105">下表列出可以為繫結檔案中的這個節點設定的屬性：</span><span class="sxs-lookup"><span data-stu-id="67662-105">The following table lists the properties that can be set for this node of a binding file:</span></span>  
  
|<span data-ttu-id="67662-106">**名稱**</span><span class="sxs-lookup"><span data-stu-id="67662-106">**Name**</span></span>|<span data-ttu-id="67662-107">**節點類型**</span><span class="sxs-lookup"><span data-stu-id="67662-107">**Node Type**</span></span>|<span data-ttu-id="67662-108">**資料類型**</span><span class="sxs-lookup"><span data-stu-id="67662-108">**Data Type**</span></span>|<span data-ttu-id="67662-109">**說明**</span><span class="sxs-lookup"><span data-stu-id="67662-109">**Description**</span></span>|<span data-ttu-id="67662-110">**限制**</span><span class="sxs-lookup"><span data-stu-id="67662-110">**Restrictions**</span></span>|<span data-ttu-id="67662-111">**註解**</span><span class="sxs-lookup"><span data-stu-id="67662-111">**Comments**</span></span>|  
|--------------|-------------------|-------------------|---------------------|----------------------|------------------|  
|[<span data-ttu-id="67662-112">傳送埠</span><span class="sxs-lookup"><span data-stu-id="67662-112">SendPort</span></span>](../core/sendport-sendportcollection-node.md)|<span data-ttu-id="67662-113">記錄</span><span class="sxs-lookup"><span data-stu-id="67662-113">Record</span></span>|<span data-ttu-id="67662-114">SendPort (ComplexType)</span><span class="sxs-lookup"><span data-stu-id="67662-114">SendPort (ComplexType)</span></span>|<span data-ttu-id="67662-115">指定隨同繫結檔案一起匯出之傳送埠的相關資訊。</span><span class="sxs-lookup"><span data-stu-id="67662-115">Specifies information about a send port that is exported with the binding file.</span></span>|<span data-ttu-id="67662-116">不需要</span><span class="sxs-lookup"><span data-stu-id="67662-116">Not required</span></span>|<span data-ttu-id="67662-117">預設值：無</span><span class="sxs-lookup"><span data-stu-id="67662-117">Default value: none</span></span>|