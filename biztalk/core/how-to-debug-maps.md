---
title: 如何偵錯對應 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: d1ee1e26-fced-4126-b48a-71007043424d
caps.latest.revision: 4
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: f30d26b7c722ea4e4896bc7d19130e41eec5c719
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "36989719"
---
# <a name="how-to-debug-maps"></a>如何偵錯對應
**偵錯對應**項功能可用於找出並修正複雜的對應問題。 本主題提供使用內嵌 XSLT 偵錯工具進行對應偵錯的逐步指示。  

> [!NOTE]
>  偵錯對應時**偵錯對應**功能會使用對應檔屬性**TestMap 輸入執行個體**並**TestMap 輸出執行個體**。 因此，建議您在偵錯對應之前先設定對應檔中的輸入與輸出執行個體屬性。  

### <a name="to-debug-a-biztalk-map"></a>若要偵錯 BizTalk 對應  

1. 在 方案總管 中，以滑鼠右鍵按一下您想要測試，然後按一下 的地圖**偵錯對應**。 [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)] 會在其編輯器中以 XSLT 格式顯示對應。  

2. 按 F10 或 F11 偵錯 XSL 程式碼。 如果您在運算質呼叫上按 F11，[!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)] 會進入該運算質的 C# 程式碼。 您可以檢視運算質中的原始程式碼本機 Windows 偵錯工具中使用的變數值。
