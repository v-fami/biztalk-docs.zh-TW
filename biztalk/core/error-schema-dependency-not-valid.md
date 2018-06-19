---
title: 錯誤-無效的結構描述相依性 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- bts10.edit.error.schemaDependencyNotValid
ms.assetid: 431278f0-6cd1-4b3f-8d87-16af4991d354
caps.latest.revision: 5
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 36326608f191b520c41cb42890aec029c432fd30
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22241390"
---
# <a name="error---schema-dependency-not-valid"></a><span data-ttu-id="634d8-102">錯誤-無效的結構描述相依性</span><span class="sxs-lookup"><span data-stu-id="634d8-102">Error - Schema Dependency Not Valid</span></span>
<span data-ttu-id="634d8-103">**錯誤碼**</span><span class="sxs-lookup"><span data-stu-id="634d8-103">**Error Code**</span></span>  
  
 <span data-ttu-id="634d8-104">BEC2009</span><span class="sxs-lookup"><span data-stu-id="634d8-104">BEC2009</span></span>  
  
 <span data-ttu-id="634d8-105">**說明**</span><span class="sxs-lookup"><span data-stu-id="634d8-105">**Explanation**</span></span>  
  
 <span data-ttu-id="634d8-106">所有相依的結構描述 (如在目前結構描述所匯入、包括或重新定義者)，必須新增至此 BizTalk 專案或存在於此專案所參考的組件中。</span><span class="sxs-lookup"><span data-stu-id="634d8-106">All dependent schemas, such as those that are imported, included, or redefined in the current schema, must be added to this BizTalk project or exist in an assembly referenced by this project.</span></span> <span data-ttu-id="634d8-107">即使結構描述**匯入**，**包含**，和**重新定義**遠端網站指定結構描述的指示詞必須新增至此 BizTalk 專案。</span><span class="sxs-lookup"><span data-stu-id="634d8-107">Even schema **import**, **include**, and **redefine** directives that specify schemas on a remote Web site must be added to this BizTalk project.</span></span>  
  
 <span data-ttu-id="634d8-108">**使用者動作**</span><span class="sxs-lookup"><span data-stu-id="634d8-108">**User Action**</span></span>  
  
 <span data-ttu-id="634d8-109">使用**加入現有項目**命令**檔案**功能表和 Microsoft® BizTalk® Server 專案，將這個結構描述所依存的所有結構描述新增至 BizTalk 專案的捷徑功能表。</span><span class="sxs-lookup"><span data-stu-id="634d8-109">Use the **Add Existing Item** command on the **File** menu and the shortcut menu for the Microsoft® BizTalk® Server project to add all schemas upon which this schema depends to the BizTalk project.</span></span> <span data-ttu-id="634d8-110">將此類結構描述新增至 BizTalk 專案前，您可能必須將它們從網站下載到本機硬碟。</span><span class="sxs-lookup"><span data-stu-id="634d8-110">You may need to download such schemas from a Web site to your local hard disk before adding them to the BizTalk project.</span></span>