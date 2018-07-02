---
title: 使用 BizTalk Server 輪詢 Oracle E-business Suite |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: a22b99a5-1715-4351-b0e0-6b8dcfacd9eb
caps.latest.revision: 4
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: b8180b3b671c87b5dcd0d41477e20b6d175f1cce
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "36974215"
---
# <a name="poll-oracle-e-business-suite-using-biztalk-server"></a>使用 BizTalk Server 輪詢 Oracle E-business Suite
您可以設定[!INCLUDE[adapteroraclebusinessshort](../../includes/adapteroraclebusinessshort-md.md)]從 Oracle 資料庫接收以輪詢為基礎的訊息。 配接器會提供兩種輪詢 Oracle 資料庫：  
  
- **使用 SELECT 陳述式**。 您可以指定要輪詢 Oracle 資料庫的簡單 SELECT 陳述式。 配接器執行 SELECT 陳述式，以指定的間隔，並將結果傳回至配接器用戶端。  
  
- **使用預存程序**。 您可以指定要輪詢 Oracle 資料庫的預存程序。 配接器會在指定的時間間隔執行預存程序，並將結果傳回至配接器用戶端。  
  
  中的兩種方法的主要差異是方式配接器用戶端指定用來輪詢 Oracle 資料庫的配接器輪詢陳述式。 簡單的 SELECT 陳述式的第一個方法的輪詢陳述式時，預存程序方法的輪詢陳述式就會是執行預存程序的要求訊息。 配接器用戶端指定任一種方法，輪詢陳述式，如**PollingInput**繫結屬性。 如需有關繫結屬性的詳細資訊，請參閱[了解 BizTalk Adapter for Oracle E-business Suite 繫結屬性](../../adapters-and-accelerators/adapter-oracle-ebs/read-about-the-biztalk-adapter-for-oracle-e-business-suite-binding-properties.md)。  
  
  在本節中的主題會提供指示，有關如何使用 SELECT 陳述式和預存程序進行輪詢。  
  
## <a name="in-this-section"></a>本節內容  
  
-   [使用 SELECT 陳述式的輪詢 Oracle E-business Suite](../../adapters-and-accelerators/adapter-oracle-ebs/poll-oracle-e-business-suite-using-select-statement.md)  
  
-   [使用預存程序輪詢 Oracle E-business Suite](../../adapters-and-accelerators/adapter-oracle-ebs/poll-oracle-e-business-suite-using-stored-procedures.md)  
  
## <a name="see-also"></a>另請參閱  
[開發 BizTalk 應用程式使用 Oracle E-business Suite 配接器](../../adapters-and-accelerators/adapter-oracle-ebs/develop-biztalk-applications-using-the-oracle-e-business-suite-adapter.md)