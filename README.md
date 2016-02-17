# cpp-syslog

This is a C++ output stream for logging to syslog.

There is also a class to redirect eg cout/clog/cerr to syslog

This code has do dependencies (except from libc and STL)

This project is supported by jp-embedded ApS and is released under the GNU GPL v3

Example:

```
include "syslog.h"

int main(int argc, char *argv[]) 
{ 
  // write to syslog 
  syslog::ostream log; 
  log << syslog::level::info << "info message 1" << std::endl; 
  log << "info message 2" << std::endl;

  // redirect cout, cerr and clog to syslog
  syslog::redirect cout_redir(std::cout);
  syslog::redirect cerr_redir(std::cerr);
  syslog::redirect clog_redir(std::clog);

  std::cout << "cout message" << std::endl;
  std::clog << "clog message" << std::endl;
  std::cerr << "cerr message" << std::endl;

  return 0;
}
```
