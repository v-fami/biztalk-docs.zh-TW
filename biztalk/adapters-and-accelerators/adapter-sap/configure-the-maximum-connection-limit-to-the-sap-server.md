---
title: 設定 SAP 伺服器的最大連接限制 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 858ed90e-b219-43cc-ad63-ae8e1eb2159a
caps.latest.revision: 3
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 853a3b78b82e242750e30099f847045ff590f125
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22215846"
---
# <a name="configure-the-maximum-connection-limit-to-the-sap-server"></a>設定 SAP 伺服器的最大連接限制
適用於 SAP 資料提供者可讓配接器用戶端控制，可以在內部開啟提供者的連接數目上限。 您可以設定環境變數，CPIC_MAX_CONV 來控制。  
  
 比方說，如果 CPIC_MAX_CONV 設為任何數值，隨時開啟的 RFC 連線的數目將小於或等於該數值。  
  
> [!NOTE]
>  數值會套用的每個個別下程序/appdomain 來設定此值。  
  
 比方說，如果應用程式中使用 Data provider for SAP，已在"x"的處理序層級上設定其環境變數，並連接到兩個不同的伺服器 A 和 B，然後最大數目的同時連線 A 和 B 會是"x"分別。